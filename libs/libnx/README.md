<NX Graphics Client and Utility Library (`libs/libnx`)>
## Overview
Top-level package for the NuttX NX graphics client library (`libnx`). It provides the shared kernel/user-mode message queue and signal abstraction macros in `nxcontext.h` and aggregates the core 2D geometry helpers (`nxglib`), high-level window drawing primitives (`nx`), multi-user client IPC proxy (`nxmu`), framed window toolkit (`nxtk`), and bitmap font management (`nxfonts`).

## Interface
- `nxcontext.h:_MQ_OPEN`, `nxcontext.h:_MQ_CLOSE`, `nxcontext.h:_MQ_SEND`, `nxcontext.h:_MQ_RECEIVE`, `nxcontext.h:_MQ_UNLINK`, `nxcontext.h:_SIG_USLEEP`, `nxcontext.h:_NX_SETERRNO`, `nxcontext.h:_NX_GETERRNO`, `nxcontext.h:_NX_GETERRVAL` - Abstracts internal `nxmq_*`/`nxsig_*` calls in kernel builds (`__KERNEL__`) versus standard POSIX `mq_*`/`usleep` and `errno` calls in user space.
- `./nx/README.md` - High-level NX window line, circle, and visibility primitives (`nx_drawline`, `nx_drawcircle`, `nx_fillcircle`, `nx_ishidden`).
- `./nxfonts/README.md` - Bitmap font registry, depth conversion (`1bpp`..`32bpp`), and thread-safe LRU glyph cache (`nxf_cache_*`).
- `./nxglib/README.md` - Fixed-point 2D geometry, rectangle set algebra, trapezoid decomposition, and RGB/YUV color conversion routines.
- `./nxmu/README.md` - Multi-user NX client connection, POSIX message queue IPC proxy, and event dispatcher (`nx_connectinstance`, `nx_eventhandler`).
- `./nxtk/README.md` - Framed window and toolbar toolkit (`nxtk_*`) layered over raw `NXWINDOW` containers.

## Invariants
- `nxcontext.h:__KERNEL__` governs whether `_MQ_*` macros return negative errno values directly (`_NX_GETERRNO(r) = -(r)`) or return `-1` and store the error code in thread-local `errno`.

## Side Effects
- `nxcontext.h:_NX_SETERRNO` mutates thread-local `errno` via `set_errno`, and the `_MQ_*` / `_SIG_USLEEP` macros perform message queue IPC and thread sleep operations when invoked by child subsystems.

## Verification
- Run: `make test`
</NX Graphics Client and Utility Library (`libs/libnx`)>
