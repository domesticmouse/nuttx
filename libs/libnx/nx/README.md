<NX Graphics Primitives (`libs/libnx/nx`)>
## Overview
Provides high-level NX window drawing and visibility primitives built on top of NXGlib geometry helpers and NX window trapezoid/fill operations. It decomposes lines and circles into trapezoids or filled rectangles and dispatches them to the underlying NX window API.

## Interface
- `nx_drawcircle.c:nx_drawcircle` - Renders a circular outline on an `NXWINDOW` by generating 16-gon points via `nxgl_circlepts` and drawing connecting line segments with `nx_drawline`.
- `nx_drawline.c:nx_drawline` - Renders a line segment of arbitrary width and end-cap style (`NX_LINECAP_NONE`, `NX_LINECAP_PT1`, `NX_LINECAP_PT2`, `NX_LINECAP_BOTH`) using `nxgl_splitline`, `nx_fill`, `nx_filltrapezoid`, and `nx_fillcircle`.
- `nx_fillcircle.c:nx_fillcircle` - Fills a circular region on an `NXWINDOW` by decomposing it into 8 horizontal trapezoids via `nxgl_circletraps` (`NCIRCLE_TRAPS`) and calling `nx_filltrapezoid`.
- `nx_ishidden.c:nx_ishidden` - Returns whether an `NXWINDOW` (`struct nxbe_window_s`) has the `NXBE_WINDOW_HIDDEN` flag set via `NXBE_ISHIDDEN`.

## Invariants
- `nx_drawline.c:nx_drawline` requires non-NULL `hwnd`, `vector`, and `color` arguments, returning `ERROR` with `errno` set to `EINVAL` when `CONFIG_DEBUG_FEATURES` is enabled, or `OK` immediately if `width < 1`.
- `nx_drawcircle.c:nx_drawcircle` and `nx_fillcircle.c:nx_fillcircle` require `radius > 0` for multi-segment/trapezoid rendering, degrading to a single pixel `nx_fill` when `radius <= 0`.

## Side Effects
- `nx_drawcircle.c:nx_drawcircle`, `nx_drawline.c:nx_drawline`, and `nx_fillcircle.c:nx_fillcircle` issue window rendering operations (`nx_fill`, `nx_filltrapezoid`, `nx_setpixel`) and mutate thread `errno` via `set_errno` on invalid parameters.

## Verification
- Run: `make test`
</NX Graphics Primitives (`libs/libnx/nx`)>
