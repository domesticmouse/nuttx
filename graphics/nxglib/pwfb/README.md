# NXGLIB Per-Window Framebuffer Rasterizers (`graphics/nxglib/pwfb`)

## Overview
Implements pixel-depth-templated (`NXGLIB_SUFFIX` for 1, 2, 4, 8, 16, 24, and 32 bpp) 2D rasterization primitives operating on per-window backing framebuffers (`struct nxbe_window_s` where `bwnd->fbmem` and `bwnd->stride` define the window's RAM buffer). Used when `CONFIG_NX_RAMBACKED` is enabled so window contents can be rendered and updated independently of display hardware planes.

## Interface
- `[pwfb_setpixel.c:pwfb_setpixel]` (`NXGL_FUNCNAME(pwfb_setpixel, NXGLIB_SUFFIX)`) - Writes a single pixel of `color` at `pos` inside the per-window framebuffer `bwnd->fbmem`
- `[pwfb_fillrectangle.c:pwfb_fillrectangle]` (`NXGL_FUNCNAME(pwfb_fillrectangle, NXGLIB_SUFFIX)`) - Fills a rectangular region `rect` in `bwnd->fbmem` with solid `color`
- `[pwfb_filltrapezoid.c:pwfb_filltrapezoid]` (`NXGL_FUNCNAME(pwfb_filltrapezoid, NXGLIB_SUFFIX)`) - Fills a trapezoid `trap` clipped to `bounds` in `bwnd->fbmem` with `color`, supporting hourglass edge crossings and optional antialiasing (`CONFIG_NX_ANTIALIASING`)
- `[pwfb_copyrectangle.c:pwfb_copyrectangle]` (`NXGL_FUNCNAME(pwfb_copyrectangle, NXGLIB_SUFFIX)`) - Copies a rectangular bitmap region `dest` from `src` (`origin`, `srcstride`) into `bwnd->fbmem`
- `[pwfb_getrectangle.c:pwfb_getrectangle]` (`NXGL_FUNCNAME(pwfb_getrectangle, NXGLIB_SUFFIX)`) - Extracts a rectangular region `rect` from `bwnd->fbmem` into caller buffer `dest` (`deststride`)
- `[pwfb_moverectangle.c:pwfb_moverectangle]` (`NXGL_FUNCNAME(pwfb_moverectangle, NXGLIB_SUFFIX)`) - Moves a rectangular region `rect` to `offset` within `bwnd->fbmem`, iterating top-down or bottom-up to preserve overlapping scanlines

## Invariants
- Requires `NXGLIB_SUFFIX` and `NXGLIB_BITSPERPIXEL` to be defined at compile time (`1`, `2`, `4`, `8`, `16`, `24`, or `32` bpp).
- Target window `bwnd` must have a valid allocated backing buffer `bwnd->fbmem` and byte row stride `bwnd->stride`.
- For `NXGLIB_BITSPERPIXEL < 8`, bit packing order within bytes follows `CONFIG_NX_PACKEDMSFIRST`.

## Side Effects
- Mutates the per-window backing framebuffer `bwnd->fbmem` in `[pwfb_setpixel.c:pwfb_setpixel]`, `[pwfb_fillrectangle.c:pwfb_fillrectangle]`, `[pwfb_filltrapezoid.c:pwfb_filltrapezoid]`, `[pwfb_copyrectangle.c:pwfb_copyrectangle]`, and `[pwfb_moverectangle.c:pwfb_moverectangle]`.
- Mutates the caller-provided buffer `dest` in `[pwfb_getrectangle.c:pwfb_getrectangle]`.

## Verification
- Run: `make test`
