# NXGLIB LCD Rasterizers (`graphics/nxglib/lcd`)

## Overview
Implements pixel-depth-templated (`NXGLIB_SUFFIX` for 1, 2, 4, 8, 16, 24, and 32 bpp) 2D rasterization primitives for serial/indirect LCD devices accessed through `struct lcd_planeinfo_s` run/area driver callbacks (`putrun`, `putarea`, `getrun`). Uses the plane's scratch run buffer (`pinfo->buffer`) and helper run-packing routines (`nxgl_fillrun`, `nxgl_copyrun`) to render pixels, rectangles, trapezoids, bitmaps, and region moves.

## Interface
- `[nxglib_setpixel.c:nxgl_setpixel]` (`NXGL_FUNCNAME(nxgl_setpixel, NXGLIB_SUFFIX)`) - Sets a single pixel at `pos` on an LCD plane via `pinfo->putrun` (performing a read-modify-write via `pinfo->getrun` when `NXGLIB_BITSPERPIXEL < 8`)
- `[nxglib_fillrectangle.c:nxgl_fillrectangle]` (`NXGL_FUNCNAME(nxgl_fillrectangle, NXGLIB_SUFFIX)`) - Fills `pinfo->buffer` using `nxgl_fillrun_*bpp` and writes each row of `rect` via `pinfo->putrun`
- `[nxglib_filltrapezoid.c:nxgl_filltrapezoid]` (`NXGL_FUNCNAME(nxgl_filltrapezoid, NXGLIB_SUFFIX)`) - Clips `trap` against `bounds`, populates `pinfo->buffer` up to the widest clipped scanline via `nxgl_fillrun_*bpp`, and writes each scanline via `pinfo->putrun`
- `[nxglib_copyrectangle.c:nxgl_copyrectangle]` (`NXGL_FUNCNAME(nxgl_copyrectangle, NXGLIB_SUFFIX)`) - Transfers a rectangular bitmap from `src` to `dest` on the LCD plane using `pinfo->putarea` (when available for `>= 8` bpp) or row-by-row `pinfo->putrun` (re-aligning sub-byte offsets via `nxgl_copyrun_*bpp` into `pinfo->buffer`)
- `[nxglib_getrectangle.c:nxgl_getrectangle]` (`NXGL_FUNCNAME(nxgl_getrectangle, NXGLIB_SUFFIX)`) - Reads a rectangular region `rect` from the LCD plane into `dest` row-by-row via `pinfo->getrun`
- `[nxglib_moverectangle.c:nxgl_moverectangle]` (`NXGL_FUNCNAME(nxgl_moverectangle, NXGLIB_SUFFIX)`) - Moves a rectangular region `rect` to `offset` on the LCD plane by reading rows into `pinfo->buffer` via `pinfo->getrun` and writing them back via `pinfo->putrun` in top-down or bottom-up order

## Invariants
- Requires `NXGLIB_SUFFIX` and `NXGLIB_BITSPERPIXEL` to be defined at compile time (`1`, `2`, `4`, `8`, `16`, `24`, or `32` bpp).
- `pinfo->buffer` must be large enough to hold a full horizontal scanline run for the widest rectangle or trapezoid rendered.
- Sub-byte bit ordering (`NXGLIB_BITSPERPIXEL < 8`) follows `CONFIG_NX_PACKEDMSFIRST`.

## Side Effects
- Invokes hardware LCD driver I/O callbacks `pinfo->putrun`, `pinfo->putarea`, and `pinfo->getrun`.
- Mutates the plane run scratch buffer `pinfo->buffer` (`[nxglib_fillrectangle.c:nxgl_fillrectangle]`, `[nxglib_filltrapezoid.c:nxgl_filltrapezoid]`, `[nxglib_copyrectangle.c:nxgl_copyrectangle]`, `[nxglib_moverectangle.c:nxgl_moverectangle]`).
- Mutates the caller-supplied buffer `dest` in `[nxglib_getrectangle.c:nxgl_getrectangle]`.

## Verification
- Run: `make test`
