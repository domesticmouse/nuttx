# NX Graphics Library (`graphics/nxglib`)

## Overview
Provides the low-level NX Graphics Library (`nxglib`) rasterization interface, bit-blit scaling/blending macros (`nxglib_bitblit.h`), scanline run-packing inline helpers (`nxglib_fillrun.h`, `nxglib_copyrun.h`), and pixel-depth-specific function prototypes (`nxglib.h`) across 1, 2, 4, 8, 16, 24, and 32 bits per pixel. Dispatches rendering operations to direct framebuffer (`fb`), serial/indirect LCD (`lcd`), per-window RAM-backed framebuffer (`pwfb`), and software cursor (`cursor`) implementations.

## Interface
- `[nxglib.h:nxgl_setpixel_1bpp]`, `[nxglib.h:nxgl_setpixel_2bpp]`, `[nxglib.h:nxgl_setpixel_4bpp]`, `[nxglib.h:nxgl_setpixel_8bpp]`, `[nxglib.h:nxgl_setpixel_16bpp]`, `[nxglib.h:nxgl_setpixel_24bpp]`, `[nxglib.h:nxgl_setpixel_32bpp]` - Device plane single-pixel write prototypes
- `[nxglib.h:pwfb_setpixel_1bpp]`, `[nxglib.h:pwfb_setpixel_2bpp]`, `[nxglib.h:pwfb_setpixel_4bpp]`, `[nxglib.h:pwfb_setpixel_8bpp]`, `[nxglib.h:pwfb_setpixel_16bpp]`, `[nxglib.h:pwfb_setpixel_24bpp]`, `[nxglib.h:pwfb_setpixel_32bpp]` - Per-window framebuffer single-pixel write prototypes (`CONFIG_NX_RAMBACKED`)
- `[nxglib.h:nxgl_fillrectangle_1bpp]` .. `[nxglib.h:nxgl_fillrectangle_32bpp]`, `[nxglib.h:pwfb_fillrectangle_1bpp]` .. `[nxglib.h:pwfb_fillrectangle_32bpp]` - Device and per-window solid rectangle fill prototypes
- `[nxglib.h:nxgl_getrectangle_1bpp]` .. `[nxglib.h:nxgl_getrectangle_32bpp]`, `[nxglib.h:pwfb_getrectangle_1bpp]` .. `[nxglib.h:pwfb_getrectangle_32bpp]` - Device and per-window rectangular region extraction prototypes
- `[nxglib.h:nxgl_filltrapezoid_1bpp]` .. `[nxglib.h:nxgl_filltrapezoid_32bpp]`, `[nxglib.h:pwfb_filltrapezoid_1bpp]` .. `[nxglib.h:pwfb_filltrapezoid_32bpp]` - Device and per-window clipped trapezoid fill prototypes
- `[nxglib.h:nxgl_moverectangle_1bpp]` .. `[nxglib.h:nxgl_moverectangle_32bpp]`, `[nxglib.h:pwfb_moverectangle_1bpp]` .. `[nxglib.h:pwfb_moverectangle_32bpp]` - Device and per-window rectangular region move prototypes
- `[nxglib.h:nxgl_copyrectangle_1bpp]` .. `[nxglib.h:nxgl_copyrectangle_32bpp]`, `[nxglib.h:pwfb_copyrectangle_1bpp]` .. `[nxglib.h:pwfb_copyrectangle_32bpp]` - Device and per-window rectangular bitmap blit prototypes
- `[nxglib.h:nxglib_cursor_draw_8bpp]` .. `[nxglib.h:nxglib_cursor_draw_32bpp]`, `[nxglib.h:nxglib_cursor_erase_8bpp]` .. `[nxglib.h:nxglib_cursor_erase_32bpp]`, `[nxglib.h:nxglib_cursor_backup_8bpp]` .. `[nxglib.h:nxglib_cursor_backup_32bpp]` - Software cursor draw, erase, and background backup prototypes (`CONFIG_NX_SWCURSOR`)
- `[nxglib_bitblit.h:NXGL_FUNCNAME]`, `[nxglib_bitblit.h:NXGL_SCALEX]`, `[nxglib_bitblit.h:NXGL_REMAINDERX]`, `[nxglib_bitblit.h:NXGL_ALIGNDOWN]`, `[nxglib_bitblit.h:NXGL_ALIGNUP]`, `[nxglib_bitblit.h:NXGL_MULTIPIXEL]`, `[nxglib_bitblit.h:NXGL_MEMSET]`, `[nxglib_bitblit.h:NXGL_MEMCPY]`, `[nxglib_bitblit.h:NXGL_BLEND]` - Depth-dependent pixel scaling, byte alignment, memory copy/fill, and RGB antialiasing blend macros
- `[nxglib_fillrun.h:nxgl_fillrun_1bpp]`, `[nxglib_fillrun.h:nxgl_fillrun_2bpp]`, `[nxglib_fillrun.h:nxgl_fillrun_4bpp]`, `[nxglib_fillrun.h:nxgl_fillrun_8bpp]`, `[nxglib_fillrun.h:nxgl_fillrun_16bpp]`, `[nxglib_fillrun.h:nxgl_fillrun_24bpp]`, `[nxglib_fillrun.h:nxgl_fillrun_32bpp]` - Inline scanline run-buffer solid color fill helpers
- `[nxglib_copyrun.h:nxgl_copyrun_1bpp]`, `[nxglib_copyrun.h:nxgl_copyrun_2bpp]`, `[nxglib_copyrun.h:nxgl_copyrun_4bpp]` - Inline sub-byte bit-shifting scanline copy helpers for unaligned 1/2/4 bpp runs
- [./cursor/README.md](./cursor/README.md) - Software cursor backup, rendering, and erasure rasterizers (`CONFIG_NX_SWCURSOR`)
- [./fb/README.md](./fb/README.md) - Direct linear framebuffer (`struct fb_planeinfo_s`) 2D rasterizers
- [./lcd/README.md](./lcd/README.md) - Indirect/serial LCD (`struct lcd_planeinfo_s`) run-based 2D rasterizers
- [./pwfb/README.md](./pwfb/README.md) - Per-window RAM-backed (`struct nxbe_window_s`) 2D rasterizers (`CONFIG_NX_RAMBACKED`)

## Invariants
- `[nxglib_bitblit.h:NXGLIB_BITSPERPIXEL]` must be defined (`1`, `2`, `4`, `8`, `16`, `24`, or `32`) before including `nxglib_bitblit.h`, `nxglib_fillrun.h`, or `nxglib_copyrun.h`.
- Antialiasing (`CONFIG_NX_ANTIALIASING`) is supported only when `NXGLIB_BITSPERPIXEL >= 16`; `nxglib_bitblit.h` undefines `CONFIG_NX_ANTIALIASING` for lower color depths.
- `[nxglib_copyrun.h:nxgl_copyrun_1bpp]`, `[nxglib_copyrun.h:nxgl_copyrun_2bpp]`, and `[nxglib_copyrun.h:nxgl_copyrun_4bpp]` assert via `DEBUGASSERT` that `remainder` is strictly non-zero and less than the number of pixels per byte (`8`, `4`, or `2`).

## Side Effects
- Inline helpers `[nxglib_fillrun.h:nxgl_fillrun_1bpp]` .. `[nxglib_fillrun.h:nxgl_fillrun_32bpp]` and `[nxglib_copyrun.h:nxgl_copyrun_1bpp]` .. `[nxglib_copyrun.h:nxgl_copyrun_4bpp]` mutate the caller-provided `run` / `dest` scanline buffers.

## Verification
- Run: `make test`
