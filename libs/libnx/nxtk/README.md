<NX Framed Window Toolkit (`libs/libnx/nxtk`)>
## Overview
Implements the NX Toolkit (`NXTK`), which layers framed windows (`struct nxtk_framedwindow_s`) with borders, an optional top toolbar sub-window, and a client interior sub-window on top of raw `NXWINDOW` containers. It intercepts container events via `g_nxtkcb`, clips coordinates to sub-window bounds, draws window frames, and routes mouse, keyboard, position, and redraw events to the appropriate client or toolbar callbacks.

## Interface
- `nxtk.h:struct nxtk_framedwindow_s` - Internal framed window state containing the base `struct nxbe_window_s wnd`, client sub-window rectangle (`fwrect`), toolbar rectangle (`tbrect`), and respective callbacks (`fwcb`, `tbcb`).
- `nxtk_events.c:g_nxtkcb` - `struct nx_callback_s` vtable registered on the underlying `NXWINDOW` to dispatch redraw, position, mouse, keyboard, and window events.
- `nxtk_openwindow.c:nxtk_openwindow`, `nxtk_closewindow.c:nxtk_closewindow`, `nxtk_opentoolbar.c:nxtk_opentoolbar`, `nxtk_closetoolbar.c:nxtk_closetoolbar` - Opens and closes framed windows (`NXTKWINDOW`) and their attached toolbars.
- `nxtk_openwindow.c:g_bordercolor1`, `nxtk_openwindow.c:g_bordercolor2`, `nxtk_openwindow.c:g_bordercolor3` - Global border color arrays initialized from `CONFIG_NXTK_BORDERCOLOR1..3`.
- `nxtk_bitmapwindow.c:nxtk_bitmapwindow`, `nxtk_drawcirclewindow.c:nxtk_drawcirclewindow`, `nxtk_drawlinewindow.c:nxtk_drawlinewindow`, `nxtk_fillcirclewindow.c:nxtk_fillcirclewindow`, `nxtk_filltrapwindow.c:nxtk_filltrapwindow`, `nxtk_fillwindow.c:nxtk_fillwindow`, `nxtk_getwindow.c:nxtk_getwindow`, `nxtk_movewindow.c:nxtk_movewindow` - Clipped drawing, blitting, and pixel readback operations for the client sub-window.
- `nxtk_bitmaptoolbar.c:nxtk_bitmaptoolbar`, `nxtk_drawcircletoolbar.c:nxtk_drawcircletoolbar`, `nxtk_drawlinetoolbar.c:nxtk_drawlinetoolbar`, `nxtk_fillcircletoolbar.c:nxtk_fillcircletoolbar`, `nxtk_filltoolbar.c:nxtk_filltoolbar`, `nxtk_filltraptoolbar.c:nxtk_filltraptoolbar`, `nxtk_gettoolbar.c:nxtk_gettoolbar`, `nxtk_movetoolbar.c:nxtk_movetoolbar`, `nxtk_toolbarbounds.c:nxtk_toolbarbounds` - Clipped drawing, blitting, readback, and bounds query operations for the toolbar sub-window.
- `nxtk_block.c:nxtk_block`, `nxtk_getposition.c:nxtk_getposition`, `nxtk_ishidden.c:nxtk_ishidden`, `nxtk_lower.c:nxtk_lower`, `nxtk_modal.c:nxtk_modal`, `nxtk_raise.c:nxtk_raise`, `nxtk_setposition.c:nxtk_setposition`, `nxtk_setsize.c:nxtk_setsize`, `nxtk_setvisibility.c:nxtk_setvisibility`, `nxtk_synch.c:nxtk_synch` - Window control, geometry, z-order, visibility, and synchronization wrappers.
- `nxtk_containerclip.c:nxtk_containerclip`, `nxtk_drawframe.c:nxtk_drawframe`, `nxtk_setsubwindows.c:nxtk_setsubwindows`, `nxtk_subwindowclip.c:nxtk_subwindowclip`, `nxtk_subwindowmove.c:nxtk_subwindowmove` - Internal geometry clipping, sub-window layout calculation, and border frame rendering helpers.

## Invariants
- All sub-window drawing and movement helpers clip coordinates against `fwnd->fwrect` or `fwnd->tbrect` using `nxtk_subwindowclip` and `nxtk_subwindowmove` so client and toolbar operations cannot overwrite border frames or adjacent sub-windows.
- `nxtk_events.c:nxtk_redraw` and `nxtk_toolbarbounds.c:nxtk_toolbarbounds` assert non-NULL window handles, callbacks, and rectangle pointers via `DEBUGASSERT`.

## Side Effects
- `nxtk_openwindow.c:nxtk_openwindow` allocates `struct nxtk_framedwindow_s` on the user heap via `lib_uzalloc` and delegates window registration to `nx_constructwindow`.
- `nxtk_opentoolbar.c:nxtk_opentoolbar` and `nxtk_closetoolbar.c:nxtk_closetoolbar` recompute sub-window rectangles (`nxtk_setsubwindows`) and request full window redraws (`nx_redrawreq`).
- Drawing, geometry, and event functions invoke underlying `nx_*` window APIs and mutate thread `errno` via `set_errno`.

## Verification
- Run: `make test`
</NX Framed Window Toolkit (`libs/libnx/nxtk`)>
