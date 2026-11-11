# src (`nuttx/arch/ceva/src`)

## Overview
Architectural grouping for `nuttx/arch/ceva/src`, coordinating 3 component subdirectories (`common`, `xc5`, `xm6`).

## Subdirectories & Boundaries
- `common`: [./common/README.md](./common/README.md) - Hardware abstraction and architecture package for `common` under `nuttx/arch/ceva/src/common`, providing 3 header file(s) and 29 source file(s) (including `ceva_internal.h`, `mpu.h`, `vintc.h`, `ceva_board.c`).
- `xc5`: [./xc5/README.md](./xc5/README.md) - Hardware abstraction and architecture package for `xc5` (XC5 Configuration Options) under `nuttx/arch/ceva/src/xc5`, providing 2 header file(s) and 7 source file(s) (including `cpm.h`, `psu.h`, `xc5_hardfault.c`, `xc5_icache.c`).
- `xm6`: [./xm6/README.md](./xm6/README.md) - Hardware abstraction and architecture package for `xm6` (XM6 Configuration Options) under `nuttx/arch/ceva/src/xm6`, providing 1 header file(s) and 6 source file(s) (including `cpm.h`, `xm6_hardfault.c`, `xm6_icache.c`, `xm6_initialstate.c`).

## Interface
- `[Makefile:CHIP_CSRCS]`
- `[Makefile:CMN_CSRCS]`
- `[Makefile:HEAD_ASRC]`
- `[Makefile:CSRCS]`
- `[Makefile:ASRCS]`
- [./common/README.md](./common/README.md)
- [./xc5/README.md](./xc5/README.md)
- [./xm6/README.md](./xm6/README.md)

## Invariants
- `[ceva_board.c:#error]` Compile-time configuration constraint: CONFIG_BOARD_LATE_INITIALIZE is required for late initialization
- `[ceva_createstack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[ceva_exit.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[ceva_fork.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[ceva_heap.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[ceva_heap.c:#error]` Compile-time configuration constraint: CONFIG_ARCH_NR_MEMORY must between 1 to 4

## Side Effects
- `[ceva_internal.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[ceva_internal.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[ceva_internal.h:modifyreg32]` Performs atomic read-modify-write updates on 32-bit MMIO registers
- `[ceva_modifyreg16.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[ceva_modifyreg32.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[ceva_modifyreg32.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)

## Verification
- Run: `make test`
