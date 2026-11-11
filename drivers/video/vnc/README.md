# VNC Framebuffer Server (`drivers/video/vnc`)

## Overview
Implements a Remote Framebuffer (RFB / VNC) server integrated with the NuttX framebuffer subsystem (`vnc_fbdev.c`, `vnc_server.c`). Supports RFB protocol handshaking (`vnc_negotiate.c`), Raw and RRE rectangle encodings (`vnc_raw.c`, `vnc_rre.c`), pixel format conversion (`vnc_color.c`), dirty rectangle update queuing (`vnc_updater.c`), and remote keyboard and pointer/touch event injection (`vnc_receiver.c`, `vnc_kbd.c`, `vnc_keymap.c`, `vnc_touch.c`).

## Interface
- `[vnc_fbdev.c:vnc_fbinitialize]`, `[vnc_fbdev.c:vnc_fb_register]`, `[vnc_fbdev.c:vnc_fb_unregister]` - Initializes the VNC virtual framebuffer (`struct fb_vtable_s`), starts the VNC server kernel thread for the specified display index, and binds mouse/keyboard callbacks.
- `[vnc_server.c:vnc_server]` - Per-display VNC server daemon that listens on TCP port `5900 + display` and manages client sessions (`struct vnc_session_s`).
- `[vnc_negotiate.c:vnc_negotiate]`, `[vnc_negotiate.c:vnc_client_pixelformat]` - Performs RFB protocol version negotiation, security handshaking, and pixel format configuration.
- `[vnc_updater.c:vnc_start_updater]`, `[vnc_updater.c:vnc_stop_updater]`, `[vnc_updater.c:vnc_update_rectangle]` - Manages the asynchronous framebuffer update thread and dirty rectangle queue.
- `[vnc_receiver.c:vnc_receiver]`, `[vnc_receiver.c:vnc_client_encodings]`, `[vnc_receiver.c:vnc_read_remainder]` - Processes incoming client RFB messages (SetPixelFormat, SetEncodings, FramebufferUpdateRequest, KeyEvent, PointerEvent, ClientCutText).
- `[vnc_raw.c:vnc_raw]`, `[vnc_rre.c:vnc_rre]`, `[vnc_rre.c:vnc_rre8]`, `[vnc_rre.c:vnc_rre16]`, `[vnc_rre.c:vnc_rre32]` - Encodes and transmits framebuffer rectangles using Raw or Rise-and-Run-length Encoding (RRE).
- `[vnc_color.c:vnc_convert_rgb8_222]`, `[vnc_color.c:vnc_convert_rgb8_332]`, `[vnc_color.c:vnc_convert_rgb16_555]`, `[vnc_color.c:vnc_convert_rgb16_565]`, `[vnc_color.c:vnc_convert_rgb32_888]` - Converts local framebuffer pixels into the remote VNC client's negotiated pixel format.
- `[vnc_kbd.c:vnc_kbd_register]`, `[vnc_kbd.c:vnc_kbd_unregister]`, `[vnc_kbd.c:vnc_kbd_event]`, `[vnc_keymap.c:vnc_key_map]`, `[vnc_touch.c:vnc_touch_register]`, `[vnc_touch.c:vnc_touch_unregister]`, `[vnc_touch.c:vnc_touch_event]` - Translates X11 keysyms and pointer coordinates from the VNC client into NuttX keyboard and touchscreen uinput/input driver events.

## Invariants
- `[vnc_fbdev.c:vnc_fbinitialize]` and framebuffer vtable callbacks assert `DEBUGASSERT(display >= 0 && display < RFB_MAX_DISPLAYS)` and `DEBUGASSERT(planeno == 0)`.
- `[vnc_raw.c:vnc_raw]` asserts `DEBUGASSERT(size <= CONFIG_VNCSERVER_UPDATE_BUFSIZE)`.
- `[vnc_color.c:vnc_ColorMap]` helpers assert `DEBUGASSERT(session != NULL && rect != NULL && maxcolors <= 8 && colors != NULL)`.

## Side Effects
- `[vnc_fbdev.c:vnc_fbinitialize]` allocates the backing framebuffer plane in kernel memory and spawns the `vnc_server` kernel thread (`kthread_create`).
- `[vnc_server.c:vnc_server]` opens kernel TCP sockets (`psock_socket`, `psock_bind`, `psock_listen`, `psock_accept`) and transmits/receives RFB packets over the network (`psock_send`, `psock_recv`).
- `[vnc_kbd.c:vnc_kbd_register]` and `[vnc_touch.c:vnc_touch_register]` register virtual keyboard and touch input devices.

## Verification
- Run: `make test`
