# AI Engine Driver (`drivers/aie`)

## Overview
Implements the upper-half character driver for AI Engine (AIE) accelerators, binding an architecture-specific `aie_lowerhalf_s` implementation to a VFS device node and forwarding session lifecycle and `ioctl` commands.

## Interface
- `ai_engine.c:aie_register` - Allocates an `ai_engine.c:aie_upperhalf_s` instance and registers an AI Engine character device at `path`.
- `ai_engine.c:aie_upperhalf_s` - Upper-half state structure encapsulating the open reference count, mutual exclusion lock, and pointer to the `aie_lowerhalf_s` lower half.

## Invariants
- `ai_engine.c:aie_register` asserts `path != NULL` and `lower != NULL` before allocating the upper-half driver.
- Open, close, and `ioctl` operations assert `upper != NULL` and `upper->lower != NULL` (`ai_engine.c:aie_upperhalf_s`).
- Reference counting (`upper->crefs`) is guarded against overflow (`UINT8_MAX`) and only invokes `lower->ops->init` on first open (`crefs == 0`) and `lower->ops->deinit` on last close (`crefs == 1`).

## Side Effects
- Acquires `upper->lock` via `nxmutex_lock` during `open`, `close`, and `ioctl` calls (`ai_engine.c:aie_upperhalf_s`).
- Allocates upper-half state via `kmm_malloc` and registers a VFS character driver via `register_driver` (`ai_engine.c:aie_register`).
- Invokes hardware-specific lower-half `init`, `deinit`, and `ioctl` callbacks (`ai_engine.c:aie_register`).

## Verification
- Run: `make test`
