# Userspace Socket Proxy (`net/usrsock`)

## Overview
The `net/usrsock` component implements the Userspace Socket (`CONFIG_NET_USRSOCK`) kernel proxy in NuttX. It provides a `struct sock_intf_s` implementation (`g_usrsock_sockif`) that serializes POSIX socket operations (`socket`, `bind`, `connect`, `listen`, `accept`, `sendmsg`, `recvmsg`, `getsockopt`, `setsockopt`, `getsockname`, `getpeername`, `ioctl`, `shutdown`, `close`) into request messages forwarded over `/dev/usrsock` (or RPMsg usrsock) to a userspace networking daemon, and processes asynchronous response and event messages returned by the daemon.

## Interface
- `[usrsock.h:enum usrsock_conn_state_e]` - Lifecycle states of a usrsock connection (`USRSOCK_CONN_STATE_UNINITIALIZED`, `USRSOCK_CONN_STATE_INPROGRESS`, `USRSOCK_CONN_STATE_READY`, `USRSOCK_CONN_STATE_ABORTED`, `USRSOCK_CONN_STATE_CONNECTING`).
- `[usrsock.h:struct usrsock_conn_s]` - Kernel proxy connection structure tracking `state`, daemon socket descriptor `usockid`, event `flags`, and active request/response exchange state (`resp`).
- `[usrsock.h:struct usrsock_reqstate_s]` - Synchronous request wait context holding `conn`, `cb`, `recvsem`, `result`, `completed`, and `unlock`.
- `[usrsock.h:struct usrsock_data_reqstate_s]` - Extended request context for responses carrying variable-length data payloads (`valuelen`, `valuelen_nontrunc`).
- `[usrsock_sockif.c:g_usrsock_sockif]` - Socket interface operations table (`struct sock_intf_s`) for usrsock sockets.
- `[usrsock_conn.c:usrsock_initialize]` - Initializes the usrsock connection pool (`[usrsock_conn.c:usrsock_alloc]`, `[usrsock_conn.c:usrsock_free]`, `[usrsock_conn.c:usrsock_nextconn]`, and `[usrsock_conn.c:usrsock_active]` manage `struct usrsock_conn_s` instances).
- `[usrsock_devif.c:usrsock_do_request]` - Serializes and dispatches a request (`iovec` array) to the `/dev/usrsock` driver.
- `[usrsock_devif.c:usrsock_setup_request_callback]` - Initializes a `struct usrsock_reqstate_s` callback prior to sending a request (`[usrsock_devif.c:usrsock_setup_data_request_callback]` and `[usrsock_devif.c:usrsock_teardown_request_callback]` manage data request and teardown state; `[usrsock_devif.c:usrsock_setup_datain]` registers output `iovec` buffers for daemon reply data).
- `[usrsock_event.c:usrsock_event]` - Dispatches event flags (`USRSOCK_EVENT_*`) from the daemon to a `struct usrsock_conn_s`.
- `[usrsock_socket.c:usrsock_socket]` - Sends `USRSOCK_REQUEST_SOCKET` to the daemon (`[usrsock_close.c:usrsock_close]` sends `USRSOCK_REQUEST_CLOSE`).
- `[usrsock_bind.c:usrsock_bind]` - Sends `USRSOCK_REQUEST_BIND` (`[usrsock_connect.c:usrsock_connect]` sends `USRSOCK_REQUEST_CONNECT`; `[usrsock_listen.c:usrsock_listen]` sends `USRSOCK_REQUEST_LISTEN`; `[usrsock_accept.c:usrsock_accept]` sends `USRSOCK_REQUEST_ACCEPT`).
- `[usrsock_poll.c:usrsock_poll]` - Manages `poll`/`select` event notifications for a usrsock socket.
- `[usrsock_sendmsg.c:usrsock_sendmsg]` - Sends `USRSOCK_REQUEST_SENDTO` (`[usrsock_recvmsg.c:usrsock_recvmsg]` sends `USRSOCK_REQUEST_RECVFROM`).
- `[usrsock_getsockopt.c:usrsock_getsockopt]` - Sends `USRSOCK_REQUEST_GETSOCKOPT` (`[usrsock_setsockopt.c:usrsock_setsockopt]` sends `USRSOCK_REQUEST_SETSOCKOPT`).
- `[usrsock_getsockname.c:usrsock_getsockname]` - Sends `USRSOCK_REQUEST_GETSOCKNAME` (`[usrsock_getpeername.c:usrsock_getpeername]` sends `USRSOCK_REQUEST_GETPEERNAME`).
- `[usrsock_ioctl.c:usrsock_ioctl]` - Sends `USRSOCK_REQUEST_IOCTL` (`[usrsock_shutdown.c:usrsock_shutdown]` sends `USRSOCK_REQUEST_SHUTDOWN`).

## Invariants
- Only one request may be in flight on a given `[usrsock.h:struct usrsock_conn_s]` at any time, enforced by acquiring `conn->resp.sem` in `[usrsock_devif.c:usrsock_do_request]` and matching daemon responses against the 64-bit exchange ID `conn->resp.xid`.

## Side Effects
- Forwards request `iovec` payloads to the `/dev/usrsock` character driver (`usrsock_request`), blocks calling threads on `req->recvsem` with the connection lock temporarily released, and copies daemon response payloads into `conn->resp.datain`.

## Verification
- Run: `make test`
