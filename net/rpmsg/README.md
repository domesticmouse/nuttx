# RPMsg Sockets (`net/rpmsg`)

## Overview
The `net/rpmsg` component implements the `AF_RPMSG` (`PF_RPMSG`, `CONFIG_NET_RPMSG`) inter-processor socket protocol family in NuttX. Built on top of OpenAMP/RPMsg endpoints (`struct rpmsg_endpoint`), it provides `SOCK_STREAM` and `SOCK_DGRAM` sockets for zero-configuration communication between tasks running on different CPU cores (`rp_cpu`, `rp_name`), complete with circular buffer flow control (`struct circbuf_s`) and `poll`/`select` notifications.

## Interface
- `[rpmsg.h:g_rpmsg_sockif]` - Socket interface operations table (`struct sock_intf_s`) for `PF_RPMSG`.
- `[rpmsg_sockif.c:struct rpmsg_socket_conn_s]` - RPMsg socket connection structure managing the `struct rpmsg_endpoint`, local/remote `struct sockaddr_rpmsg`, circular receive buffer (`recvdata`), flow-control counters (`sendsize`, `recvsize`), and backlog list.
- `[rpmsg_sockif.c:struct rpmsg_socket_sync_s]` - Handshake header (`RPMSG_SOCKET_CMD_SYNC`) exchanging receive buffer capacity (`size`) and peer credentials (`pid`, `uid`, `gid`).
- `[rpmsg_sockif.c:struct rpmsg_socket_data_s]` - Data frame header (`RPMSG_SOCKET_CMD_DATA`) carrying consumed RX position (`pos`), payload length (`len`), and data bytes.
- `[rpmsg_sockif.c:struct rpmsg_socket_shutdown_s]` - Shutdown control message (`RPMSG_SOCKET_CMD_SHUTDOWN`) propagating `SHUT_RD`/`SHUT_WR` state to the remote core.

## Invariants
- `rpmsg_socket_listen` in `[rpmsg_sockif.c:g_rpmsg_sockif]` requires `psock->s_type == SOCK_STREAM`, `_SS_ISBOUND(conn->sconn.s_flags)`, and `backlog > 0`.
- Outbound data transmissions respect remote circular buffer space calculated by `rpmsg_socket_get_space(conn)` while holding `conn->sendlock`.

## Side Effects
- Registers RPMsg device lifecycle callbacks (`rpmsg_register_callback` / `rpmsg_unregister_callback`) and creates/destroys hardware/shared-memory RPMsg endpoints (`rpmsg_create_ept` / `rpmsg_destroy_ept`).
- Allocates per-connection `struct circbuf_s` buffers on the kernel heap and transmits IPC messages across CPU cores via `rpmsg_send_nocopy`.

## Verification
- Run: `make test`
