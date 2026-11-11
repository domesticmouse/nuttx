# NXGLIB Software Cursor Rasterizers (`graphics/nxglib/cursor`)

## Overview
Provides pixel-depth-templated (`NXGLIB_SUFFIX`) software cursor backup, drawing, and erasure routines for linear framebuffer devices when `CONFIG_NX_SWCURSOR` is enabled. Operates directly on the back-end plane memory (`be->plane[planeno].pinfo.fbmem`) and cursor background save buffer (`be->cursor.bkgd`).

## Interface
- `[nxglib_cursor_backup.c:nxglib_cursor_backup]` (`NXGL_FUNCNAME(nxglib_cursor_backup, NXGLIB_SUFFIX)`) - Copies the intersection of the modified display `bounds`, display background, and `be->cursor.bounds` from device framebuffer memory into `be->cursor.bkgd`
- `[nxglib_cursor_draw.c:nxglib_cursor_draw]` (`NXGL_FUNCNAME(nxglib_cursor_draw, NXGLIB_SUFFIX)`) - Renders packed 2-bit-per-pixel cursor glyph data (`be->cursor.image`) onto device framebuffer memory using the 3-color palette (`be->cursor.color1`, `color2`, `color3`) while skipping transparent pixels (`0`)
- `[nxglib_cursor_erase.c:nxglib_cursor_erase]` (`NXGL_FUNCNAME(nxglib_cursor_erase, NXGLIB_SUFFIX)`) - Restores the saved background pixels from `be->cursor.bkgd` back into device framebuffer memory over the intersected cursor region

## Invariants
- Compiled only when `CONFIG_NX_SWCURSOR` is defined and `NXGLIB_SUFFIX` / `NXGL_PIXEL_T` are instantiated by the build system.
- All operations clip against both `be->cursor.bounds` and `be->bkgd.bounds` before intersecting with the dirty `bounds` rectangle; no memory access occurs if the resulting intersection is a null rectangle (`nxgl_nullrect`).
- Source cursor glyphs in `be->cursor.image` are packed at 2 bits per pixel (4 pixels per byte, MSB first), where pixel value `0` is transparent and `1..3` map to `be->cursor.color1..3` (`[nxglib_cursor_draw.c:nxbe_map_color]`).

## Side Effects
- `[nxglib_cursor_backup.c:nxglib_cursor_backup]` mutates the cursor background buffer `be->cursor.bkgd`.
- `[nxglib_cursor_draw.c:nxglib_cursor_draw]` and `[nxglib_cursor_erase.c:nxglib_cursor_erase]` directly mutate hardware/device framebuffer memory (`be->plane[planeno].pinfo.fbmem`).

## Verification
- Run: `make test`
