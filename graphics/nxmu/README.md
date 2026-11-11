# NX Multi-User Server (`graphics/nxmu`)

## Overview
Implements the NX Multi-User (`nxmu`) windowing server daemon and IPC message dispatcher. Serializes multi-client access to display hardware over POSIX message queues (`nxmq_open`, `nxmq_receive`, `nxmq_send`), manages the server connection lifecycle, allocates per-window RAM framebuffers (`CONFIG_NX_RAMBACKED`), routes mouse/touchscreen (`CONFIG_NX_XYINPUT`) and keyboard (`CONFIG_NX_KBD`) input events to target windows, and delegates window hierarchy and rendering operations to the NX back-end (`nxbe`).

## Interface
- `[nxmu.h:struct nxmu_state_s]` - Top-level NX server state structure embedding `struct nxbe_state_s be` as its first member (allowing direct pointer casts) and the server's loopback connection `struct nxmu_conn_s conn`
- `[nxmu_start.c:nxmu_start]` - Spawns the `"NX Server"` kernel thread (`nx_server`) for a given `display` and `plane`, initializing the underlying LCD, framebuffer, VNC, or custom board graphics device
- `[nxmu_server.c:nx_runinstance]` - Main NX server event loop: configures the back-end (`nxbe_configure`, `nxbe_colormap`), opens the server message queue (`mqname`), draws the initial background, and dispatches `enum nx_svrmsg_e` (`NX_SVRMSG_*`) and background `NX_CLIMSG_REDRAW` messages
- `[nxmu_openwindow.c:nxmu_openwindow]` - Initializes a newly opened `struct nxbe_window_s`, allocates per-window RAM framebuffer pages (`mm_pgalloc`) or heap memory (`kumm_malloc`) when `NXBE_ISRAMBACKED(wnd)` is set, inserts the window into the Z-order stack (respecting modal top windows), and reports initial position and mouse state
- `[nxmu_requestbkgd.c:nxmu_requestbkgd]`, `[nxmu_releasebkgd.c:nxmu_releasebkgd]` - Grants a client connection control and callbacks over the background window (`be->bkgd`) or restores background ownership back to the server
- `[nxmu_redraw.c:nxmu_redraw]`, `[nxmu_redraw.c:nxmu_redrawreq]` - Updates a rectangular window region either immediately from its per-window framebuffer via `nxbe_flush` (`NXBE_ISRAMBACKED`) or by sending an `NX_CLIMSG_REDRAW` request to the client
- `[nxmu_reportposition.c:nxmu_reportposition]` - Sends an `NX_CLIMSG_NEWPOSITION` message containing updated window position, size, and screen bounds to the owning client
- `[nxmu_sendclient.c:nxmu_sendclient]`, `[nxmu_sendclientwindow.c:nxmu_sendclientwindow]` - Sends a message at `NX_CLIMSG_PRIO` priority to a client message queue (`conn->swrmq`), suppressing delivery if the target window is marked blocked (`NXBE_ISBLOCKED(wnd)`)
- `[nxmu_mouse.c:nxmu_mouseinit]`, `[nxmu_mouse.c:nxmu_mousein]`, `[nxmu_mouse.c:nxmu_mousereport]` - Tracks global pointer coordinates (`g_mpos`), button state (`g_mbutton`), and active drag window (`g_mwnd`), routing window-relative `NX_CLIMSG_MOUSEIN` messages to the topmost visible window supporting mouse callbacks (`CONFIG_NX_XYINPUT`)
- `[nxmu_kbdin.c:nxmu_kbdin]` - Packages incoming keyboard character bytes into a variable-length `NX_CLIMSG_KBDIN` message and delivers it to `nxmu->be.topwnd` (`CONFIG_NX_KBD`)

## Invariants
- Compile-time check in `[nxmu.h:CONFIG_MQ_MAXMSGSIZE]` requires `CONFIG_MQ_MAXMSGSIZE >= 64`.
- `struct nxbe_state_s be` must remain the first field of `[nxmu.h:struct nxmu_state_s]` so `struct nxbe_state_s *` and `struct nxmu_state_s *` can be cast interchangeably.
- `[nxmu_start.c:nxmu_start]` asserts `(unsigned)display < CONFIG_NX_NDISPLAYS` and `(unsigned)plane < CONFIG_NX_NPLANES`, and cannot be called from the IDLE thread because it sleeps via `nxsched_usleep`.
- When `NXBE_STATE_ISMODAL(be)` is active, newly opened non-hidden windows are inserted immediately below `be->topwnd` rather than above it (`[nxmu_openwindow.c:nxmu_openwindow]`).
- Mouse drag sequences (`oldbuttons != 0`) remain locked to the originating window `g_mwnd` (revalidated via `[nxmu_mouse.c:nxmu_revalidate_g_mwnd]`) until all buttons are released (`[nxmu_mouse.c:nxmu_mousein]`).

## Side Effects
- Creates kernel threads (`kthread_create`) and sleeps (`nxsched_usleep`) in `[nxmu_start.c:nxmu_start]`, and initializes display hardware via `board_graphics_setup`, `board_lcd_initialize`, `vnc_fb_register`, or `up_fbinitialize`.
- Opens, closes, reads, and writes POSIX message queues via `nxmq_open`, `nxmq_close`, `nxmq_receive`, and `nxmq_send`, and posts completion semaphores (`sem_done`) on `NX_SVRMSG_GETRECTANGLE` and `NX_SVRMSG_BITMAP` (`[nxmu_server.c:nx_runinstance]`).
- Allocates per-window backing memory from the page pool (`mm_pgalloc`) or user heap (`kumm_malloc`) in `[nxmu_openwindow.c:nxmu_openwindow]`, and allocates transient keyboard messages via `kmm_malloc` / `kmm_free` in `[nxmu_kbdin.c:nxmu_kbdin]`.

## Verification
- Run: `make test`
