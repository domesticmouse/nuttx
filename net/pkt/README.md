# Raw Packet Sockets (`net/pkt`)

## Overview
The `net/pkt` component implements raw L2 packet sockets (`PF_PACKET` / `AF_PACKET`, `CONFIG_NET_PKT`) in NuttX. It allows applications to receive and transmit raw link-layer frames (such as Ethernet frames) directly on network interfaces, supporting both buffered (`CONFIG_NET_PKT_WRITE_BUFFERS`) and unbuffered transmission modes.

## Interface
- `[pkt.h:struct pkt_conn_s]` - Connection structure for `PF_PACKET` sockets storing `ifindex`, `eth_type`, flags, `readahead` RX queue, and `write_q` TX queue.
- `[pkt.h:struct pkt_poll_s]` - Poll context structure associating a `struct pkt_conn_s`, `struct net_driver_s`, and `struct pollfd`.
- `[pkt_sockif.c:g_pkt_sockif]` - Socket interface operations table (`struct sock_intf_s`) for `PF_PACKET`.
- `[pkt_conn.c:pkt_alloc]` - Allocates a new `struct pkt_conn_s` (`[pkt_conn.c:pkt_free]` releases it and purges queued buffers).
- `[pkt_conn.c:pkt_active]` - Finds an active `PF_PACKET` connection matching an incoming frame on `dev` (`[pkt_conn.c:pkt_nextconn]` iterates active connections).
- `[pkt_conn.c:pkt_conn_list_lock]` - Acquires the global packet connection list lock (`[pkt_conn.c:pkt_conn_list_unlock]` releases it).
- `[pkt_input.c:pkt_input]` - Delivers an inbound L2 frame on `dev` to all matching `PF_PACKET` sockets.
- `[pkt_callback.c:pkt_callback]` - Handles network device events (`PKT_NEWDATA`, `PKT_POLL`) for packet connections.
- `[pkt_finddev.c:pkt_find_device]` - Resolves the `struct net_driver_s` bound to `conn->ifindex`.
- `[pkt_poll.c:pkt_poll]` - Polls a `struct pkt_conn_s` for pending outbound frames on `dev`.
- `[pkt_netpoll.c:pkt_pollsetup]` - Sets up `poll`/`select` monitoring on a `PF_PACKET` socket (`[pkt_netpoll.c:pkt_pollteardown]` tears it down).
- `[pkt_recvmsg.c:pkt_recvmsg]` - Receives a raw L2 frame from `conn->readahead`.
- `[pkt_sendmsg_buffered.c:pkt_sendmsg]` - Enqueues and transmits a raw frame using write buffers (`[pkt_sendmsg_unbuffered.c:pkt_sendmsg]` transmits directly when write buffering is disabled; `[pkt_sockif.c:pkt_sendmsg_is_valid]` validates `sendmsg` arguments).
- `[pkt_getsockopt.c:pkt_getsockopt]` - Queries `SOL_PACKET` socket options (`[pkt_setsockopt.c:pkt_setsockopt]` sets `SOL_PACKET` options such as `PACKET_ADD_MEMBERSHIP` / `PACKET_DROP_MEMBERSHIP`).

## Invariants
- `[pkt_conn.c:pkt_active]`, `[pkt_conn.c:pkt_nextconn]`, `[pkt_callback.c:pkt_callback]`, `[pkt_poll.c:pkt_poll]`, and `[pkt_input.c:pkt_input]` must be called with the network lock held.
- Mutations to the active packet connection list require holding `[pkt_conn.c:pkt_conn_list_lock]`.

## Side Effects
- Clones and enqueues inbound L2 frames into `conn->readahead` and outbound frames into `conn->write_q`.
- Enables/disables promiscuous or all-multicast modes on `dev` via `SIOCSIFFLAGS` in `[pkt_setsockopt.c:pkt_setsockopt]` and triggers device transmission via `netdev_txnotify_dev`.

## Verification
- Run: `make test`
