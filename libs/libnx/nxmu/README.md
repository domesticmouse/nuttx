<NX Multi-User Client Library (`libs/libnx/nxmu`)>
## Overview
Implements the client-side IPC proxy and event dispatcher for the NuttX Multi-User (`nxmu`) graphics server. Client calls serialize window management, rendering, cursor, and input commands into `struct nxsvrmsg_s` messages sent over POSIX message queues (`_MQ_SEND`), while `nx_eventhandler` receives server callbacks (`_MQ_RECEIVE`) and dispatches them to client window handlers.

## Interface
- `nx_connect.c:nx_connectinstance` and `nx_disconnect.c:nx_disconnect` - Establishes and tears down an `NXHANDLE` (`struct nxmu_conn_s`) client connection with the NX server message queue.
- `nx_eventhandler.c:nx_eventhandler` and `nx_eventnotify.c:nx_eventnotify` - Receives and dispatches `NX_CLIMSG_*` messages (`NX_CLIMSG_CONNECTED`, `NX_CLIMSG_DISCONNECTED`, `NX_CLIMSG_REDRAW`, `NX_CLIMSG_NEWPOSITION`, `NX_CLIMSG_MOUSEIN`, `NX_CLIMSG_KBDIN`, `NX_CLIMSG_EVENT`) or registers a `struct sigevent` notification via `mq_notify`.
- `nx_openwindow.c:nx_openwindow`, `nx_constructwindow.c:nx_constructwindow`, `nx_closewindow.c:nx_closewindow`, `nx_requestbkgd.c:nx_requestbkgd`, `nx_releasebkgd.c:nx_releasebkgd` - Allocates, initializes, and closes raw `NXWINDOW` (`struct nxbe_window_s`) and background window instances.
- `nx_bitmap.c:nx_bitmap`, `nx_fill.c:nx_fill`, `nx_filltrapezoid.c:nx_filltrapezoid`, `nx_getrectangle.c:nx_getrectangle`, `nx_move.c:nx_move`, `nx_setbgcolor.c:nx_setbgcolor`, `nx_setpixel.c:nx_setpixel` - Sends window drawing, blitting, and pixel readback requests to the server.
- `nx_block.c:nx_block`, `nx_getposition.c:nx_getposition`, `nx_lower.c:nx_lower`, `nx_modal.c:nx_modal`, `nx_raise.c:nx_raise`, `nx_redrawreq.c:nx_redrawreq`, `nx_setposition.c:nx_setposition`, `nx_setsize.c:nx_setsize`, `nx_setvisibility.c:nx_setvisibility`, `nx_synch.c:nx_synch` - Manages window z-order, geometry, visibility, modal state, redraw requests, and server synchronization.
- `nx_cursor.c:nxcursor_enable`, `nx_cursor.c:nxcursor_setimage`, `nx_cursor.c:nxcursor_setposition`, `nx_cursor.c:nxcursor_get_position` - Controls hardware/software cursor visibility, image, and position.
- `nx_kbdchin.c:nx_kbdchin`, `nx_kbdin.c:nx_kbdin`, `nx_mousein.c:nx_mousein` - Injects keyboard and mouse input events into the NX server for focus distribution.
- `nxmu_sendserver.c:nxmu_sendserver` and `nxmu_sendwindow.c:nxmu_sendwindow` - Internal IPC transport helpers that transmit `NX_SVRMSG_*` messages to the server connection queue (`conn->cwrmq`), unless blocked by `NXBE_STATE_BLOCKED`.

## Invariants
- `nx_connect.c:g_nxliblock` protects the monotonic global client ID counter `nx_connect.c:g_nxcid` (`cid > 0`, with ID 0 reserved for the server).
- `nx_eventhandler.c:nx_connected` asserts via `DEBUGASSERT` that `conn->state == NX_CLISTATE_NOTCONNECTED` prior to transitioning to `NX_CLISTATE_CONNECTED`.
- `nx_bitmap.c:nx_bitmap` and `nx_getrectangle.c:nx_getrectangle` synchronize asynchronous shared-memory transfers using a local semaphore (`nxsem_init`, `nxsem_wait`, `nxsem_destroy`) before returning to the caller.

## Side Effects
- Opens, sends, receives, closes, and unlinks POSIX message queues via `_MQ_OPEN`, `_MQ_SEND`, `_MQ_RECEIVE`, `_MQ_CLOSE`, `_MQ_UNLINK`, and `mq_notify`.
- Allocates and frees client connection, window, and keyboard message buffers via `lib_uzalloc`, `lib_ufree`, `lib_malloc`, and `lib_free`.
- Acquires mutex `g_nxliblock` (`nxmutex_lock` / `nxmutex_unlock`), blocks on semaphores (`nxsem_wait`), and sets thread `errno` (`set_errno`, `_NX_SETERRNO`).

## Verification
- Run: `make test`
</NX Multi-User Client Library (`libs/libnx/nxmu`)>
