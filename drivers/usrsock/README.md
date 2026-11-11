# Userspace Socket (Usrsock) Drivers (`drivers/usrsock`)

## Overview
Implements the NuttX `/dev/usrsock` character device bridge (`usrsock_dev.c`) and RPMSG cross-core transport (`usrsock_rpmsg.c`, `usrsock_rpmsg_server.c`) that forward kernel networking socket requests (`usrsock_request`) to a userspace daemon or remote processor hosting the TCP/IP or cellular stack.

## Interface
- `[usrsock_dev.c:usrsock_register]`, `[usrsock_dev.c:usrsock_request]` - Registers `/dev/usrsock` and dispatches kernel socket I/O vector requests to the userspace daemon listening on `/dev/usrsock`.
- `[usrsock_rpmsg.c:usrsock_register]`, `[usrsock_rpmsg.c:usrsock_request]` - RPMSG client implementation of `usrsock` that forwards kernel socket requests over an OpenAMP RPMSG endpoint (`"rpmsg-usrsock"`) to a remote processor.
- `[usrsock_rpmsg_server.c:usrsock_rpmsg_server_initialize]` - RPMSG server daemon/worker that receives remote `usrsock` requests and executes them against the local kernel socket layer (`psock_*`) or local `/dev/usrsock`.

## Invariants
- `[usrsock_dev.c:usrsock_request]` and file operations assert `DEBUGASSERT(dev)` on `g_usrsockdev`.
- `[usrsock_rpmsg_server.c:usrsock_rpmsg_server_initialize]` packet handlers assert `DEBUGASSERT(len > offset)` when parsing fragmented read/recvfrom payloads.

## Side Effects
- `[usrsock_dev.c:usrsock_register]` registers `/dev/usrsock` via `register_driver` and wakes waiting userspace daemons via `poll_notify` and semaphores (`nxsem_post`).
- `[usrsock_rpmsg.c:usrsock_register]` and `[usrsock_rpmsg_server.c:usrsock_rpmsg_server_initialize]` register RPMSG callbacks (`rpmsg_register_callback`), create RPMSG endpoints, allocate TX buffers (`rpmsg_get_tx_payload_buffer`), and perform cross-core IPC transfers.
- `[usrsock_dev.c:usrsock_write]` passes response headers and data payloads back into the networking stack via `usrsock_response`.

## Verification
- Run: `make test`
