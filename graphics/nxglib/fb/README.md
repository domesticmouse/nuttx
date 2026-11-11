# NXGLIB Framebuffer Rasterizers (`graphics/nxglib/fb`)

## Overview
Implements pixel-depth-templated (`NXGLIB_SUFFIX` for 1, 2, 4, 8, 16, 24, and 32 bpp) 2D rasterization primitives operating directly on linear RAM/VRAM framebuffers (`struct fb_planeinfo_s`). Supports pixel setting, rectangular fills, trapezoidal fills with fixed-point (`b16_t`) edge stepping and optional antialiasing (`CONFIG_NX_ANTIALIASING`), bitmap blitting, rectangular region extraction, and overlap-safe rectangular moves.

## Interface
- `[nxglib_setpixel.c:nxgl_setpixel]` (`NXGL_FUNCNAME(nxgl_setpixel, NXGLIB_SUFFIX)`) - Writes a single pixel of `color` at `pos` in `pinfo->fbmem`, applying sub-byte bit masking for depths `< 8` bpp
- `[nxglib_fillrectangle.c:nxgl_fillrectangle]` (`NXGL_FUNCNAME(nxgl_fillrectangle, NXGLIB_SUFFIX)`) - Fills a rectangular region `rect` in `pinfo->fbmem` with solid `color`
- `[nxglib_filltrapezoid.c:nxgl_filltrapezoid]` (`NXGL_FUNCNAME(nxgl_filltrapezoid, NXGLIB_SUFFIX)`) - Fills a trapezoid `trap` clipped to `bounds` in `pinfo->fbmem` with `color`, supporting hourglass edge crossings and optional edge blending (`CONFIG_NX_ANTIALIASING`)
- `[nxglib_copyrectangle.c:nxgl_copyrectangle]` (`NXGL_FUNCNAME(nxgl_copyrectangle, NXGLIB_SUFFIX)`) - Blits a rectangular region `dest` from an external source bitmap (`src`, `origin`, `srcstride`) into `pinfo->fbmem`
- `[nxglib_getrectangle.c:nxgl_getrectangle]` (`NXGL_FUNCNAME(nxgl_getrectangle, NXGLIB_SUFFIX)`) - Copies a rectangular region `rect` from `pinfo->fbmem` into a caller buffer (`dest`, `deststride`)
- `[nxglib_moverectangle.c:nxgl_moverectangle]` (`NXGL_FUNCNAME(nxgl_moverectangle, NXGLIB_SUFFIX)`) - Copies a rectangular region `rect` to `offset` within `pinfo->fbmem`, choosing top-down or bottom-up row iteration to avoid clobbering overlapping regions

## Invariants
- Requires `NXGLIB_SUFFIX` and `NXGLIB_BITSPERPIXEL` to be defined at compile time (`1`, `2`, `4`, `8`, `16`, `24`, or `32` bpp).
- For `NXGLIB_BITSPERPIXEL < 8`, bit packing order within bytes follows `CONFIG_NX_PACKEDMSFIRST` (MSB-first when defined, LSB-first otherwise).
- Callers must ensure target rectangles (`dest`, `rect`, `pos`, `offset`) lie within the valid dimensions of `pinfo->fbmem` (except `nxgl_filltrapezoid`, which clips against `bounds`).

## Side Effects
- Mutates framebuffer memory (`pinfo->fbmem`) in `[nxglib_setpixel.c:nxgl_setpixel]`, `[nxglib_fillrectangle.c:nxgl_fillrectangle]`, `[nxglib_filltrapezoid.c:nxgl_filltrapezoid]`, `[nxglib_copyrectangle.c:nxgl_copyrectangle]`, and `[nxglib_moverectangle.c:nxgl_moverectangle]`.
- Mutates the caller-supplied destination buffer `dest` in `[nxglib_getrectangle.c:nxgl_getrectangle]`.

## Verification
- Run: `make test`
