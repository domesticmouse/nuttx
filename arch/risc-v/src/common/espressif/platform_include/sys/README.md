# sys (`nuttx/arch/risc-v/src/common/espressif/platform_include/sys`)

## Overview
Hardware abstraction and architecture package for `sys` under `nuttx/arch/risc-v/src/common/espressif/platform_include/sys`, providing 1 header file(s) and 0 source file(s) (including `lock.h`).

## Interface
- `[lock.h:_lock_init_recursive]`
- `[lock.h:_lock_close]`
- `[lock.h:_lock_close_recursive]`
- `[lock.h:_lock_acquire]`
- `[lock.h:_lock_acquire_recursive]`
- `[lock.h:_lock_try_acquire]`
- `[lock.h:_lock_try_acquire_recursive]`
- `[lock.h:_lock_release]`
- `[lock.h:_lock_release_recursive]`
- `[lock.h:__lock]`
- `[lock.h:_lock_t]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
