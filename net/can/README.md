# SocketCAN (`net/can`)

## Overview
The `net/can` component implements the SocketCAN (`PF_CAN`) protocol family for NuttX. It provides connection management, hardware/software CAN filter matching, IOB buffer pooling, device polling, and protocol implementations for both raw CAN frames (`CAN_RAW`) and the ISO 15765-2 transport protocol (`CAN_ISOTP`).

## Interface
- `[can.h:struct can_conn_s]` - SocketCAN connection structure storing bound interface index, read-ahead/write queues, CAN filters, and ISO-TP state.
- `[can.h:struct can_poll_s]` - Poll context structure linking a SocketCAN connection, device callback, and `struct pollfd`.
- `[can_sockif.c:can_sockif]` - Top-level `PF_CAN` socket interface (`struct sock_intf_s`) dispatching to `CAN_RAW` or `CAN_ISOTP`.
- `[can_raw.c:g_can_raw_sockif]` - Socket interface operations table for `CAN_RAW` sockets.
- `[can_isotp.c:g_can_isotp_sockif]` - Socket interface operations table for `CAN_ISOTP` sockets.
- `[can.c:can_conn_init]` - Initializes a `struct can_conn_s` and inserts it into the active SocketCAN connection list.
- `[can.c:can_conn_uninit]` - Removes a connection from the active list and releases its queued IOB buffers.
- `[can.c:can_conn_bind]` - Binds a SocketCAN connection to a network interface specified by `struct sockaddr_can`.
- `[can.c:can_get_ifindex]` - Returns the bound network device for a `struct can_conn_s`.
- `[can.c:can_conn_next]` - Iterates through active SocketCAN connections.
- `[can.c:can_conn_list_lock]` - Acquires the global SocketCAN connection list lock (`[can.c:can_conn_list_unlock]` releases it).
- `[can.c:can_callback]` - Handles network device events (`CAN_NEWDATA`, `CAN_POLL`) for active CAN connections.
- `[can.c:can_recviob]` - Dequeues the next received CAN frame IOB chain from a connection's `readahead` queue.
- `[can.c:can_datahandler]` - Enqueues an incoming CAN IOB chain onto a connection's `readahead` queue.
- `[can.c:can_poll]` - Polls a `struct can_conn_s` for queued outbound frames ready for transmission on `dev`.
- `[can.c:can_readahead_signal]` - Signals waiting readers via workqueue notifiers when new CAN frames arrive.
- `[can.c:can_sendbuffer_notify]` - Signals waiting writers when CAN write buffer space becomes available.
- `[can.c:can_input]` - Dispatches an inbound CAN frame from `dev` to all matching SocketCAN connections.
- `[can_bufpool.c:can_iob_timedalloc]` - Allocates an IOB with optional timeout for CAN frame buffering.
- `[can_bufpool.c:can_iob_clone]` - Clones a CAN frame IOB chain for delivery to multiple listening sockets.

## Invariants
- Protocol-specific `match` and `input` callbacks on `[can.h:struct can_conn_s]` must be assigned before calling `[can.c:can_conn_init]`.
- Traversal and mutation of the global SocketCAN connection list require holding `[can.c:can_conn_list_lock]`.
- `[can.c:can_recviob]` transfers ownership of the returned IOB chain to the caller, who must free it via `iob_free_chain`.

## Side Effects
- Enqueues inbound CAN frames into `readahead` and outbound frames into `write_q` on `[can.h:struct can_conn_s]`.
- Signals `sndsem` and workqueue read-ahead notifiers (`[can.c:can_readahead_signal]`, `[can.c:can_sendbuffer_notify]`) and triggers device TX notifications via `netdev_txnotify_dev`.

## Verification
- Run: `make test`
