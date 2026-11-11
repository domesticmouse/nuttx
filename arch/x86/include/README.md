# include (`nuttx/arch/x86/include`)

## Overview
Hardware abstraction and architecture package for `include` under `nuttx/arch/x86/include`, providing 7 header file(s) and 0 source file(s) (including `arch.h`, `inttypes.h`, `io.h`, `irq.h`).

## Subdirectories & Boundaries
- `i486`: [./i486/README.md](./i486/README.md) - Hardware abstraction and architecture package for `i486` under `nuttx/arch/x86/include/i486`, providing 6 header file(s) and 0 source file(s) (including `arch.h`, `inttypes.h`, `io.h`, `irq.h`).
- `qemu`: [./qemu/README.md](./qemu/README.md) - Hardware abstraction and architecture package for `qemu` under `nuttx/arch/x86/include/qemu`, providing 2 header file(s) and 0 source file(s) (including `arch.h`, `irq.h`).

## Interface
- `[irq.h:STACKFRAME_ALIGN]`
- `[irq.h:up_interrupt_context]`
- `[irq.h:up_getusrpc]`
- `[irq.h:up_getusrsp]`
- `[syscall.h:sys_call6]`
- `[syscall.h:SYS_syscall]`
- [./i486/README.md](./i486/README.md)
- [./qemu/README.md](./qemu/README.md)

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
