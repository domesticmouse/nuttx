# NX Window Manager Back-End (`graphics/nxbe`)

## Overview
Implements the NX Window Manager Back-End (`nxbe`), responsible for maintaining the Z-ordered window stack (`topwnd` down to `bkgd`), decomposing partially occluded rectangles via non-overlapping clipping (`nxbe_clipper`), binding pixel-depth-specific `nxglib` rasterizer vtables (`nxbe_configure`), managing software/hardware cursor overlays (`nxbe_cursor_*`), synchronizing per-window RAM-backed framebuffers (`CONFIG_NX_RAMBACKED`), and notifying external display consumers (`CONFIG_NX_UPDATE`).

## Interface
- `[nxbe.h:struct nxbe_state_s]` - Overall back-end windowing state holding `flags` (`NXBE_STATE_MODAL`), cursor state (`struct nxbe_cursor_s`), window Z-order list (`topwnd`, `bkgd`), `bgcolor`, `struct fb_videoinfo_s vinfo`, and per-plane rasterizer vtables (`plane[CONFIG_NX_NPLANES]`)
- `[nxbe.h:struct nxbe_plane_s]` - Per-plane descriptor bundling `struct nxbe_dev_vtable_s dev`, `struct nxbe_pwfb_vtable_s pwfb` (`CONFIG_NX_RAMBACKED`), `struct nxbe_cursorops_s cursor` (`CONFIG_NX_SWCURSOR`), `driver`, and `pinfo`
- `[nxbe.h:struct nxbe_clipops_s]` - Clipping callback pair (`visible`, `obscured`) invoked by `nxbe_clipper`
- `[nxbe_configure.c:nxbe_configure]` - Queries video controller and plane metadata (`dev->getvideoinfo`, `dev->getplaneinfo`) and populates `be->plane[i].dev`, `pwfb`, and `cursor` vtables matching each plane's bits-per-pixel (`1`, `2`, `4`, `8`, `16`, `24`, or `32` bpp)
- `[nxbe_colormap.c:nxbe_colormap]` - Allocates and programs a 216-color ($6 \times 6 \times 6$ RGB cube) hardware palette via `dev->putcmap` (`CONFIG_FB_CMAP`)
- `[nxbe_clipper.c:nxbe_clipper]`, `[nxbe_clipper.c:nxbe_clipnull]` - Stack-based rectangular occlusion clipper that splits `dest` against all overlapping higher-Z windows (`currw->above`) in the specified `NX_CLIPORDER_*` order and invokes `cops->visible` and `cops->obscured`
- `[nxbe_closewindow.c:nxbe_closewindow]` - Unlinks a non-background window from the Z-order hierarchy, clears modal state if applicable, triggers `nxbe_redrawbelow`, frees per-window backing pages/heap (`mm_pgfree` / `kumm_free`), and frees `wnd`
- `[nxbe_raise.c:nxbe_raise]`, `[nxbe_lower.c:nxbe_lower]`, `[nxbe_modal.c:nxbe_modal]` - Reorders windows in the Z-stack (respecting modal top windows and immovable background) and triggers redraws of newly exposed regions
- `[nxbe_setvisibility.c:nxbe_setvisibility]`, `[nxbe_setvisibility.c:nxbe_show_window]`, `[nxbe_setvisibility.c:nxbe_hide_window]` - Toggles `NXBE_ISHIDDEN(wnd)`, inserting or removing `wnd` from the active Z-order list and redrawing affected regions
- `[nxbe_setposition.c:nxbe_setposition]`, `[nxbe_setsize.c:nxbe_setsize]` - Updates window origin or dimensions, reallocates per-window backing framebuffers (`nxbe_realloc`), notifies the client via `nxmu_reportposition`, and redraws the union of old and new bounds via `nxbe_redrawbelow`
- `[nxbe_isvisible.c:nxbe_isvisible]` - Tests whether an absolute screen coordinate `pos` lies within `wnd->bounds` and is unoccluded by any window above `wnd`
- `[nxbe_redraw.c:nxbe_redraw]`, `[nxbe_redrawbelow.c:nxbe_redrawbelow]` - Clips `rect` against higher windows and dispatches `nxmu_redraw` for visible regions of `wnd` (or `wnd` and all windows below it)
- `[nxbe_setpixel.c:nxbe_setpixel]`, `[nxbe_fill.c:nxbe_fill]`, `[nxbe_filltrapezoid.c:nxbe_filltrapezoid]`, `[nxbe_move.c:nxbe_move]`, `[nxbe_bitmap.c:nxbe_bitmap]`, `[nxbe_bitmap.c:nxbe_bitmap_dev]`, `[nxbe_getrectangle.c:nxbe_getrectangle]` - Clipped window drawing, blitting, region movement, and pixel extraction operations across per-window framebuffers and physical device planes
- `[nxbe_flush.c:nxbe_flush]` - Flushes a modified per-window framebuffer region to the display device via `nxbe_bitmap_dev` and refreshes the software cursor via `nxbe_cursor_backupdraw_all` (`CONFIG_NX_RAMBACKED`)
- `[nxbe_cursor.c:nxbe_cursor_enable]`, `[nxbe_cursor.c:nxbe_cursor_setimage]`, `[nxbe_cursor.c:nxbe_cursor_setposition]` - Enables/disables the cursor, updates its 2-bpp glyph image and background save buffer (`kmm_realloc`), and moves the cursor position (`CONFIG_NX_SWCURSOR` / `CONFIG_NX_HWCURSOR`)
- `[nxbe_cursor_backupdraw.c:nxbe_cursor_backupdraw]`, `[nxbe_cursor_backupdraw.c:nxbe_cursor_backupdraw_dev]`, `[nxbe_cursor_backupdraw.c:nxbe_cursor_backupdraw_all]`, `[nxbe_cursor_backupdraw.c:nxbe_cursor_backupdraw_devall]` - Saves updated device pixels into `be->cursor.bkgd` and redraws the software cursor over modified regions (`CONFIG_NX_SWCURSOR`)
- `[nxbe_notify_rectangle.c:nxbe_notify_rectangle]` - Converts an updated `nxgl_rect_s` into `struct fb_area_s` and invokes `dev->updatearea` (`CONFIG_NX_UPDATE`)

## Invariants
- The background window (`&be->bkgd`) is permanently anchored at the bottom of the Z-order hierarchy (`be->bkgd.below == NULL`) and must never be closed or hidden (`DEBUGASSERT(wnd != &be->bkgd)` in `[nxbe_closewindow.c:nxbe_closewindow]` and `[nxbe_setvisibility.c:nxbe_hide_window]`).
- Hidden windows (`NXBE_ISHIDDEN(wnd)`) are unlinked from the `above`/`below` Z-order list and never write directly to hardware device planes (`plane->dev.*`), though RAM-backed hidden windows continue updating `wnd->fbmem`.
- When `NXBE_STATE_ISMODAL(be)` is set, `be->topwnd` is the modal window (`NXBE_ISMODAL(be->topwnd)`), and non-modal windows cannot be raised or shown above `be->topwnd->below` (`[nxbe_raise.c:nxbe_raise]`, `[nxbe_setvisibility.c:nxbe_show_window]`).

## Side Effects
- Mutates hardware display planes via `be->plane[i].dev.*`, `dev->putcmap`, and `dev->updatearea`, and mutates per-window RAM buffers (`wnd->fbmem`) via `be->plane[i].pwfb.*`.
- Allocates and frees dynamic clipping stacks (`kmm_realloc`, `kmm_free` in `[nxbe_clipper.c:nxbe_clipper]`), colormap tables (`kmm_malloc`, `kmm_free` in `[nxbe_colormap.c:nxbe_colormap]`), cursor background buffers (`kmm_realloc` in `[nxbe_cursor.c:nxbe_cursor_setimage]`), and window structures / per-window framebuffers (`mm_pgalloc`, `mm_pgfree`, `kumm_malloc`, `kumm_free` in `[nxbe_closewindow.c:nxbe_closewindow]` and `[nxbe_setsize.c:nxbe_realloc]`).
- Sends client redraw and position notifications via `nxmu_redraw`, `nxmu_redrawreq`, and `nxmu_reportposition`.

## Verification
- Run: `make test`
