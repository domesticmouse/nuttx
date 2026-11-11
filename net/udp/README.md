# UDP (`net/udp`)

## Overview
The `net/udp` component implements the User Datagram Protocol (UDP) for IPv4 and IPv6 in NuttX. It manages connectionless and connected `SOCK_DGRAM` sockets (`struct udp_conn_s`), ephemerally allocated and explicitly bound UDP ports, read-ahead RX datagram queuing (`readahead`) with source address/interface/timestamp metadata headers, optional outbound write buffering (`struct udp_wrbuffer_s`), broadcast/multicast delivery, and socket polling/notifications.

## Interface
- `[udp.h:struct udp_conn_s]` - UDP connection control block containing local/remote IPv4/IPv6 addresses (`u`), ports (`lport`, `rport`), `flags`, `rcvbufs`, `readahead` IOB queue, and optional `write_q` write buffer queue.
- `[udp.h:struct udp_poll_s]` - Poll context structure associating a `struct udp_conn_s`, `struct net_driver_s`, and `struct pollfd`.
- `[udp.h:struct udp_wrbuffer_s]` - Outbound UDP write buffer node (`wb_node`, `wb_dest`, `wb_destlen`, `wb_iob`).
- `[udp_conn.c:udp_alloc]` - Allocates a new `struct udp_conn_s` (`[udp_conn.c:udp_free]` frees it and drains `readahead` and `write_q`).
- `[udp_conn.c:udp_active]` - Finds an active `struct udp_conn_s` matching an incoming UDP datagram (`[udp_conn.c:udp_nextconn]` iterates active connections; `[udp_conn.c:udp_conn_list_lock]` and `[udp_conn.c:udp_conn_list_unlock]` lock/unlock the connection list).
- `[udp_conn.c:udp_select_port]` - Allocates an unused ephemeral local UDP port (`[udp_conn.c:udp_bind]` and `[udp_conn.c:udp_connect]` bind local and remote addresses/ports).
- `[udp_close.c:udp_close]` - Closes a UDP socket, drains pending TX buffers, leaves any joined IGMP multicast groups, and frees the connection.
- `[udp_input.c:udp_ipv4_input]` - Processes incoming IPv4 UDP datagrams, cloning and delivering copies to all matching sockets (`[udp_input.c:udp_ipv6_input]` processes IPv6 UDP datagrams).
- `[udp_send.c:udp_send]` - Formats UDP and IPv4/IPv6 headers and checksums on `dev->d_iob` for transmission.
- `[udp_sendto_buffered.c:psock_udp_sendto]` - Buffered UDP `sendto` implementation (`[udp_sendto_buffered.c:psock_udp_cansend]` checks write buffer space; `[udp_sendto_unbuffered.c:psock_udp_sendto]` implements unbuffered direct `sendto`).
- `[udp_recvfrom.c:psock_udp_recvfrom]` - Dequeues a datagram and its prepended source metadata from `conn->readahead`.
- `[udp_callback.c:udp_callback]` - Handles network device events (`UDP_NEWDATA`, `UDP_POLL`) and enqueues incoming datagrams onto `conn->readahead`.
- `[udp_devpoll.c:udp_poll]` - Polls a `struct udp_conn_s` for pending outbound UDP datagrams on `dev`.
- `[udp_finddev.c:udp_find_laddr_device]` - Resolves the network device matching a local bound address (`[udp_finddev.c:udp_find_raddr_device]` resolves the outgoing device for a destination address).
- `[udp_ipselect.c:udp_ipv4_select]` - Prepares IPv4 header fields on `dev` for an incoming/outgoing UDP packet (`[udp_ipselect.c:udp_ipv6_select]` prepares IPv6).
- `[udp_netpoll.c:udp_pollsetup]` - Sets up `poll`/`select` monitoring on a UDP socket (`[udp_netpoll.c:udp_pollteardown]` tears it down).
- `[udp_notifier.c:udp_readahead_notifier_setup]` - Registers a workqueue notifier for `conn->readahead` (`[udp_notifier.c:udp_notifier_teardown]` and `[udp_notifier.c:udp_readahead_signal]` manage teardown and signaling).
- `[udp_wrbuffer.c:udp_wrbuffer_alloc]` - Allocates a `struct udp_wrbuffer_s` (`[udp_wrbuffer.c:udp_wrbuffer_timedalloc]`, `[udp_wrbuffer.c:udp_wrbuffer_tryalloc]`, and `[udp_wrbuffer.c:udp_wrbuffer_release]` manage timed/non-blocking allocation and release).
- `[udp_txdrain.c:udp_txdrain]` - Waits for `conn->write_q` to drain.
- `[udp_setsockopt.c:udp_setsockopt]` - Configures `IPPROTO_UDP` options (`[udp_ioctl.c:udp_ioctl]` handles `FIONREAD` and `FIONSPACE`).

## Invariants
- `[udp_input.c:udp_ipv4_input]`, `[udp_input.c:udp_ipv6_input]`, `[udp_devpoll.c:udp_poll]`, and `[udp_send.c:udp_send]` must be called with the network lock held.
- Every datagram queued in `conn->readahead` by `[udp_callback.c:udp_callback]` is prefixed with a metadata header (`datalen`, optional `ifindex`, `src_addr_size`, `src_addr`, and optional `SO_TIMESTAMP` `struct timeval`) consumed by `[udp_recvfrom.c:psock_udp_recvfrom]`.

## Side Effects
- Allocates and frees `[udp.h:struct udp_conn_s]` and `[udp.h:struct udp_wrbuffer_s]` structures from preallocated pools or the heap, queues IOBs in `readahead` and `write_q`, generates ICMP/ICMPv6 Port Unreachable replies when no socket matches a unicast datagram, and triggers device TX notifications.

## Verification
- Run: `make test`
