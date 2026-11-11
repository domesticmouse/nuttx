# Video, Framebuffer, V4L2, and Camera Sensor Drivers (`drivers/video`)

## Overview
Implements the NuttX video and display subsystem, including the upper-half framebuffer character driver (`fb.c`) with optional boot splashscreen logos (`new_logo.c`, `nxlogo80.c`, `nxlogo160.c`, `nxlogo320.c`), Video4Linux2 (V4L2) core, capture, and memory-to-memory codec drivers (`v4l2_core.c`, `v4l2_cap.c`, `v4l2_m2m.c`), video frame buffer ring/queue management (`video_framebuff.c`), QEMU Goldfish virtual framebuffer/GPU/camera drivers (`goldfish_fb.c`, `goldfish_gpu_fb.c`, `goldfish_camera.c`), MAX7456 SPI on-screen display driver (`max7456.c`), and CMOS camera image sensor drivers (`gc0308.c`, `ov2640.c`, `isx012.c`, `isx019.c`), plus MIPI DSI and VNC subdirectories.

## Interface
- `[fb.c:fb_register]`, `[fb.c:fb_register_device]`, `[fb.c:fb_notify_vsync]`, `[fb.c:fb_peek_paninfo]`, `[fb.c:fb_remove_paninfo]`, `[fb.c:fb_paninfo_count]` - Upper-half `/dev/fbN` character driver, multi-buffer panning queue management, and VSync poll notification APIs.
- `[v4l2_core.c:video_register]`, `[v4l2_core.c:video_unregister]` - Registers and unregisters V4L2 device nodes (`/dev/videoN`).
- `[v4l2_cap.c:capture_initialize]`, `[v4l2_cap.c:capture_uninitialize]`, `[v4l2_cap.c:capture_register]`, `[v4l2_cap.c:capture_unregister]`, `[v4l2_cap.c:imgsensor_register]`, `[v4l2_cap.c:imgdata_register]` - V4L2 camera capture upper-half driver and image sensor / image data bus registration APIs.
- `[v4l2_m2m.c:codec_register]`, `[v4l2_m2m.c:codec_unregister]`, `[v4l2_m2m.c:codec_output_put_buf]`, `[v4l2_m2m.c:codec_capture_put_buf]`, `[v4l2_m2m.c:codec_queue_event]` - V4L2 memory-to-memory (M2M) hardware codec upper-half driver.
- `[video_framebuff.c:video_framebuff_init]`, `[video_framebuff.c:video_framebuff_uninit]`, `[video_framebuff.c:video_framebuff_realloc_container]`, `[video_framebuff.c:video_framebuff_free_container]`, `[video_framebuff.c:video_framebuff_is_empty]`, `[video_framebuff.c:video_framebuff_queue_container]`, `[video_framebuff.c:video_framebuff_cancel_container]`, `[video_framebuff.c:video_framebuff_capture_done]` - Container queue manager for V4L2 ring and FIFO capture buffers.
- `[goldfish_fb.c:goldfish_fb_register]`, `[goldfish_gpu_fb.c:goldfish_gpu_fb_register]`, `[goldfish_camera.c:goldfish_camera_initialize]` - QEMU Goldfish framebuffer, Goldfish pipe GPU framebuffer, and Goldfish virtual camera drivers.
- `[max7456.c:max7456_register]` - Maxim MAX7456 SPI monochrome on-screen display (OSD) character driver.
- `[gc0308.c:gc0308_initialize]`, `[ov2640.c:ov2640_initialize]`, `[isx012.c:isx012_initialize]`, `[isx012.c:isx012_uninitialize]`, `[isx019.c:isx019_initialize]`, `[isx019.c:isx019_uninitialize]` - GalaxyCore GC0308, OmniVision OV2640, and Sony ISX012/ISX019 camera image sensor drivers.
- Subdirectories:
  - [./mipidsi/README.md](./mipidsi/README.md) - MIPI DSI host, peripheral device, and packet framing framework.
  - [./vnc/README.md](./vnc/README.md) - VNC (RFB) virtual framebuffer server and remote input drivers.

## Invariants
- `[fb.c:fb_register_device]` splashscreen rendering asserts `DEBUGASSERT(SPLASHSCREEN_FMT == vinfo->fmt)`, `DEBUGASSERT(g_splscr.width <= vinfo->xres)`, and `DEBUGASSERT(g_splscr.height <= vinfo->yres)`.
- `[isx012.c:isx012_read_register]` asserts `DEBUGASSERT(regsize <= 4)` and `[isx019.c:isx019_read_register]` asserts `DEBUGASSERT(size <= ISX019_I2C_REGSIZE_MAX)`.
- `[v4l2_cap.c:capture_initialize]` requires registered `imgsensor_s` and `imgdata_s` operations before starting capture streams.

## Side Effects
- Registers `/dev/fb*`, `/dev/video*`, and `/dev/osd*` character devices via `register_driver`.
- Performs I2C (`I2C_TRANSFER`) and SPI (`SPI_EXCHANGE`) transactions to configure camera sensors and OSD memory, and programs DMA frame buffers via `imgdata_ops_s`.
- Synchronizes frame buffer queues and VSync/capture completion events using `nxmutex_lock`, `spin_lock_irqsave`, `nxsem_post`, and `poll_notify`.

## Verification
- Run: `make test`
