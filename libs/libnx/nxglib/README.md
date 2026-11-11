<NX Graphics Library (`libs/libnx/nxglib`)>
## Overview
Provides pure 2D fixed-point geometry, rectangle set algebra, trapezoid/run manipulation, and color conversion/blending routines for the NuttX NX graphics subsystem. These helper routines operate on `nxgl_point_s`, `nxgl_rect_s`, `nxgl_run_s`, `nxgl_trapezoid_s`, and pixel color formats without direct device or IPC dependencies.

## Interface
- `nxgl_area2rect.c:nxgl_area2rect` and `nxgl_rect2area.c:nxgl_rect2area` - Converts between `struct fb_area_s` (origin + width/height) and `struct nxgl_rect_s` (inclusive bounding coordinates).
- `nxglib_circlepts.c:nxgl_circlepts` and `nxglib_circletraps.c:nxgl_circletraps` - Approximates a circle of given center and radius into 16 perimeter `struct nxgl_point_s` vertices or 8 horizontal `struct nxgl_trapezoid_s` slices using `b16_t` trigonometric constants.
- `nxglib_colorcmp.c:nxgl_colorcmp` and `nxglib_colorcopy.c:nxgl_colorcopy` - Compares and copies multi-plane pixel color arrays (`nxgl_mxpixel_t[CONFIG_NX_NPLANES]`).
- `nxglib_intersecting.c:nxgl_intersecting`, `nxglib_nonintersecting.c:nxgl_nonintersecting`, `nxglib_nullrect.c:nxgl_nullrect`, `nxglib_rectadd.c:nxgl_rectadd`, `nxglib_rectcopy.c:nxgl_rectcopy`, `nxglib_rectinside.c:nxgl_rectinside`, `nxglib_rectintersect.c:nxgl_rectintersect`, `nxglib_rectoffset.c:nxgl_rectoffset`, `nxglib_rectoverlap.c:nxgl_rectoverlap`, `nxglib_rectsize.c:nxgl_rectsize`, `nxglib_rectunion.c:nxgl_rectunion` - Performs rectangle intersection, non-overlapping decomposition (`NX_TOP_NDX`, `NX_LEFT_NDX`, `NX_RIGHT_NDX`, `NX_BOT_NDX`), union, point-inclusion testing, offset translation, and dimension calculation.
- `nxglib_runcopy.c:nxgl_runcopy`, `nxglib_runoffset.c:nxgl_runoffset`, `nxglib_trapcopy.c:nxgl_trapcopy`, `nxglib_trapoffset.c:nxgl_trapoffset` - Copies and translates `b16_t` fixed-point trapezoid runs (`struct nxgl_run_s`) and trapezoids (`struct nxgl_trapezoid_s`).
- `nxglib_splitline.c:nxgl_splitline` - Decomposes a thick line (`struct nxgl_vector_s`, `linewidth`) into 3 horizontal trapezoids (`traps[3]`) or returns `1` for vertical lines and `2` for horizontal lines.
- `nxglib_vectoradd.c:nxgl_vectoradd` and `nxglib_vectsubtract.c:nxgl_vectsubtract` - Adds and subtracts 2D `struct nxgl_point_s` vectors.
- `nxglib_rgb2yuv.c:nxgl_rgb2yuv`, `nxglib_yuv2rgb.c:nxgl_yuv2rgb`, `nxglib_rgbblend.c:nxglib_rgb24_blend`, `nxglib_rgbblend.c:nxglib_rgb565_blend` - Converts between 8-bit RGB and YUV color spaces and blends foreground/background RGB24 or RGB565 colors using `ub16_t` fractional weights.

## Invariants
- `nxglib_splitline.c:nxgl_splitline` requires a positive `linewidth > 0` and non-NULL `vector` and `traps` pointers, returning `-EINVAL` otherwise.
- `nxglib_nullrect.c:nxgl_nullrect` defines an empty rectangle as one where `pt1.x > pt2.x` or `pt1.y > pt2.y`.

## Side Effects
- Mutates caller-provided output structures (`struct nxgl_rect_s`, `struct nxgl_point_s`, `struct nxgl_trapezoid_s`, `struct fb_area_s`, and RGB/YUV output pointers) in place; performs no heap allocations, locks, or I/O.

## Verification
- Run: `make test`
</NX Graphics Library (`libs/libnx/nxglib`)>
