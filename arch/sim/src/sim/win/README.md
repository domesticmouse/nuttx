# win (`nuttx/arch/sim/src/sim/win`)

## Overview
Hardware abstraction and architecture package for `win` under `nuttx/arch/sim/src/sim/win`, providing 0 header file(s) and 8 source file(s) (including `sim_errno.c`, `sim_hostfs.c`, `sim_hostirq.c`, `sim_hostmemory.c`).

## Interface
- `[sim_errno.c:host_errno_convert]`
- `[sim_errno.c:host_errno_get]`
- `[sim_errno.c:host_errno_set]`
- `[sim_hostfs.c:host_open]`
- `[sim_hostfs.c:host_close]`
- `[sim_hostfs.c:host_read]`
- `[sim_hostfs.c:host_write]`
- `[sim_hostfs.c:host_lseek]`
- `[sim_hostfs.c:host_ioctl]`
- `[sim_hostfs.c:host_sync]`
- `[sim_hostfs.c:host_dup]`
- `[sim_hostfs.c:host_fstat]`
- `[sim_hostfs.c:host_fchstat]`
- `[sim_hostfs.c:host_ftruncate]`
- `[sim_hostfs.c:host_opendir]`
- `[sim_hostfs.c:host_readdir]`
- `[sim_hostfs.c:host_rewinddir]`
- `[sim_hostfs.c:host_closedir]`
- `[sim_hostfs.c:host_statfs]`
- `[sim_hostfs.c:host_unlink]`
- `[sim_hostfs.c:host_mkdir]`
- `[sim_hostfs.c:host_rmdir]`
- `[sim_hostfs.c:host_rename]`
- `[sim_hostfs.c:host_stat]`
- `[sim_hostfs.c:host_chstat]`
- `[sim_hostfs.c:host_link]`
- `[sim_hostfs.c:host_symlink]`
- `[sim_hostfs.c:host_readlink]`
- `[sim_hostfs.c:host_lstat]`
- `[sim_hostirq.c:up_irq_flags]`

## Invariants
- `[sim_hostirq.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)

## Side Effects
- `[sim_hostirq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[sim_hostirq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)

## Verification
- Run: `make test`
