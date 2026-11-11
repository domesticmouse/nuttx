# NuttX Video, Framebuffer & Display Subsystem (`include/nuttx/video`)

## Overview
Defines the NuttX Framebuffer (`fb.h`), Video4Linux2 (`video.h`, `v4l2_cap.h`, `v4l2_m2m.h`), camera image sensor and data capture (`imgsensor.h`, `imgdata.h`), MIPI DSI host/device (`mipi_dsi.h`, `mipi_display.h`), display timing and EDID parsing (`edid.h`, `videomode.h`, `vesagtf.h`), Remote Framebuffer / VNC server (`rfb.h`, `vnc.h`), RGB color utilities (`rgbcolors.h`), and hardware video/camera driver headers.

## Interface
- `fb.h:fb_vtable_s`, `fb.h:fb_videoinfo_s`, `fb.h:fb_planeinfo_s`, `fb.h:fb_overlayinfo_s`, `fb.h:fb_cmap_s`, `fb.h:fb_area_s`, `fb.h:up_fbinitialize`, `fb.h:up_fbgetvplane`, `fb.h:up_fbuninitialize`, `fb.h:fb_register`, `fb.h:fb_register_device`, `fb.h:fb_notify_vsync`, `fb.h:FBIOGET_VIDEOINFO`, `fb.h:FBIOGET_PLANEINFO`, `fb.h:FBIOPAN_DISPLAY` - Framebuffer character driver vtable, plane/overlay descriptors, vsync pan-queue management, and `FBIO*` ioctl commands.
- `video.h:v4l2_s`, `video.h:v4l2_ops_s`, `video.h:video_register`, `video.h:video_unregister`, `v4l2_cap.h:capture_initialize`, `v4l2_cap.h:capture_register`, `v4l2_m2m.h:codec_s`, `v4l2_m2m.h:codec_ops_s`, `v4l2_m2m.h:codec_register` - V4L2 core, video capture, and memory-to-memory (`m2m`) hardware codec driver interfaces.
- `imgsensor.h:imgsensor_s`, `imgsensor.h:imgsensor_ops_s`, `imgsensor.h:imgsensor_format_s`, `imgsensor.h:imgsensor_register`, `imgdata.h:imgdata_s`, `imgdata.h:imgdata_ops_s`, `imgdata.h:imgdata_register` - Lower-half camera sensor control and frame DMA capture interfaces.
- `mipi_dsi.h:mipi_dsi_host`, `mipi_dsi.h:mipi_dsi_host_ops`, `mipi_dsi.h:mipi_dsi_device`, `mipi_dsi.h:mipi_dsi_msg`, `mipi_dsi.h:mipi_dsi_host_register`, `mipi_dsi.h:mipi_dsi_device_register`, `mipi_dsi.h:mipi_dsi_transfer`, `mipi_display.h:MIPI_DSI_VSYNC_START` - MIPI DSI bus host, panel device, and DCS/generic packet transfer APIs.
- `edid.h:edid_info_s`, `edid.h:edid_parse`, `videomode.h:videomode_s`, `videomode.h:videomode_lookup_by_name`, `vesagtf.h:vesagtf_params`, `vesagtf.h:vesagtf_mode` - Display EDID parsing, mode database lookup, and VESA Generalized Timing Formula calculation.
- `vnc.h:vnc_fbinitialize`, `vnc.h:vnc_fb_register`, `rfb.h:rfb_serverinit_s`, `rgbcolors.h:RGBTO24`, `rgbcolors.h:RGBTO16` - VNC/RFB network framebuffer server and RGB color conversion macros.
- Hardware & Emulator Drivers: `gc0308.h:gc0308_initialize`, `isx012.h:isx012_initialize`, `isx019.h:isx019_initialize`, `ov2640.h:ov2640_initialize`, `max7456.h:max7456_register`, `goldfish_fb.h:goldfish_fb_register`, `goldfish_gpu_fb.h:goldfish_gpu_fb_register`, `goldfish_camera.h:goldfish_camera_initialize`.

## Invariants
- Framebuffer drivers supporting multi-buffering must inspect the pan queue via `fb.h:fb_peek_paninfo` and retire displayed frames via `fb.h:fb_remove_paninfo` synchronized with vertical blanking (`fb.h:fb_notify_vsync`).
- `v4l2_cap.h:capture_register` requires both a registered `imgdata.h:imgdata_s` DMA capture backend and at least one `imgsensor.h:imgsensor_s` camera sensor instance.

## Side Effects
- `fb.h:fb_register_device`, `video.h:video_register`, and `mipi_dsi.h:mipi_dsi_host_register` create `/dev/fb*`, `/dev/video*`, and `/dev/dsi*` character device nodes.
- `vnc.h:vnc_fbinitialize` spawns a background VNC server thread listening on TCP sockets for RFB protocol clients.

## Verification
- Run: `make test`
