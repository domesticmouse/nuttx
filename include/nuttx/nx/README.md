# NuttX Graphics Windowing Subsystem (`include/nuttx/nx`)

## Overview
Provides the public API and internal server/back-end headers for the NuttX Graphics (`NX`) windowing system, including raw windows, framed toolkit windows (`NXTK`), multi-user client/server message queues (`NXMU`), bitmap font rendering (`NXFONTS`), cursor control, graphics primitives (`NXGLIB`), and virtual terminal emulation (`NXTERM`).

## Interface
- `nx.h:NXHANDLE`, `nx.h:NXWINDOW`, `nx.h:nx_callback_s`, `nx.h:nx_event_e`, `nx.h:nx_runinstance`, `nx.h:nx_connectinstance`, `nx.h:nx_disconnect`, `nx.h:nx_eventhandler`, `nx.h:nx_openwindow`, `nx.h:nx_closewindow`, `nx.h:nx_setposition`, `nx.h:nx_setsize`, `nx.h:nx_fill`, `nx.h:nx_move`, `nx.h:nx_bitmap` - Core NX server connection, event loop, raw window lifecycle, and drawing operations.
- `nxtk.h:NXTKWINDOW`, `nxtk.h:nxtk_openwindow`, `nxtk.h:nxtk_closewindow`, `nxtk.h:nxtk_opentoolbar`, `nxtk.h:nxtk_closetoolbar`, `nxtk.h:nxtk_fillwindow`, `nxtk.h:nxtk_bitmapwindow` - Framed window and toolbar APIs with automatic border and client-area management.
- `nxtypes.h:nxgl_mxpixel_t`, `nxtypes.h:nxgl_coord_t`, `nxtypes.h:nxgl_point_s`, `nxtypes.h:nxgl_size_s`, `nxtypes.h:nxgl_rect_s`, `nxtypes.h:nxgl_vector_s`, `nxtypes.h:nxgl_trapezoid_s` - Fundamental coordinate, pixel, rectangle, vector, and trapezoid geometry types.
- `nxglib.h:nxgl_rgb2yuv`, `nxglib.h:nxgl_yuv2rgb`, `nxglib.h:nxgl_rectcopy`, `nxglib.h:nxgl_rectintersect`, `nxglib.h:nxgl_rectunion`, `nxglib.h:nxgl_rectoverlap`, `nxglib.h:NX_DRIVERTYPE` - Low-level rectangle geometry helpers, color-space conversions, and framebuffer/LCD driver binding types.
- `nxfonts.h:FCACHE`, `nxfonts.h:nx_fontid_e`, `nxfonts.h:nx_font_s`, `nxfonts.h:nx_fontbitmap_s`, `nxfonts.h:nxf_getfonthandle`, `nxfonts.h:nxf_getbitmap`, `nxfonts.h:nxf_cache_connect`, `nxfonts.h:nxf_cache_getglyph` - Font lookup, glyph bitmap conversion (`1bpp` to `32bpp`), and glyph cache management.
- `nxcursor.h:nx_cursorimage_s`, `nxcursor.h:nxcursor_enable`, `nxcursor_setimage`, `nxcursor.h:nxcursor_setposition` - Hardware/software cursor visibility, glyph, and position control.
- `nxmu.h:nxmu_conn_s`, `nxmu.h:nxmsg_e`, `nxmu.h:nxmu_start`, `nxmu.h:nxmu_sendserver`, `nxmu.h:nxmu_sendwindow` - Multi-user server IPC message formats and message queue dispatch functions.
- `nxbe.h:nxbe_window_s`, `nxbe.h:NXBE_WINDOW_BLOCKED`, `nxbe.h:NXBE_WINDOW_RAMBACKED` - Back-end window state structure and window attribute flags.
- `nxterm.h:NXTERM`, `nxterm.h:nxterm_window_s`, `nxterm.h:nx_register`, `nxterm.h:nxtk_register`, `nxterm.h:nxtool_register`, `nxterm.h:nxterm_ioctl_tap` - Character console driver bindings rendered onto NX/NXTK windows.

## Invariants
- `nx.h:CONFIG_NX_NPLANES` and `nxglib.h:NX_DRIVERTYPE` bind the NX graphics layer to either a framebuffer (`struct fb_vtable_s`) or LCD (`struct lcd_planeinfo_s`) driver at compile time.
- When `nxbe.h:NXBE_WINDOW_BLOCKED` is set on a window (via `nx.h:nx_block` or `nxtk.h:nxtk_block`), no further queued client messages are processed for that window until unblocked for safe teardown.

## Side Effects
- Multi-user operations (`nxmu.h:nxmu_sendserver`, `nxmu.h:nxmu_sendwindow`, `nx.h:nx_connectinstance`) open and transmit POSIX message queues (`NX_DEFAULT_SERVER_MQNAME`, `NX_CLIENT_MQNAMEFMT`) between client threads and the NX server daemon.
- Drawing calls (`nx.h:nx_fill`, `nxtk.h:nxtk_fillwindow`) and terminal writes (`nxterm.h:nx_register`) mutate framebuffer/LCD memory or per-window RAM-backed buffers (`nxbe.h:NXBE_WINDOW_RAMBACKED`).

## Verification
- Run: `make test`
