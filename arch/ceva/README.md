# ceva (`nuttx/arch/ceva`)

## Overview
Architectural grouping for `nuttx/arch/ceva` (CEVA Options), coordinating 2 component subdirectories (`include`, `src`).

## Subdirectories & Boundaries
- `include`: [./include/README.md](./include/README.md) - Hardware abstraction and architecture package for `include` under `nuttx/arch/ceva/include`, providing 9 header file(s) and 0 source file(s) (including `arch.h`, `barriers.h`, `inttypes.h`, `irq.h`).
- `src`: [./src/README.md](./src/README.md) - Architectural grouping for `nuttx/arch/ceva/src`, coordinating 3 component subdirectories (`common`, `xc5`, `xm6`).

## Interface
- `[Kconfig:CONFIG_ARCH_XC5]`
- `[Kconfig:CONFIG_ARCH_XM6]`
- `[Kconfig:CONFIG_ARCH_FAMILY]`
- `[Kconfig:CONFIG_ARCH_ITCM_SIZE]`
- `[Kconfig:CONFIG_ARCH_DTCM_SIZE]`
- `[Kconfig:CONFIG_CEVA_ICACHE]`
- `[Kconfig:CONFIG_CEVA_DCACHE]`
- `[Kconfig:CONFIG_ARCH_NR_FPUS]`
- [./include/README.md](./include/README.md)
- [./src/README.md](./src/README.md)

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
