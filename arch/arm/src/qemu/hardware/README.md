# hardware (`nuttx/arch/arm/src/qemu/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/qemu/hardware`, providing 1 header file(s) and 0 source file(s) (including `qemu_memorymap.h`).

## Interface
- `[qemu_memorymap.h:ARMV7A_PGTABLE_MAPPING]`

## Invariants
- `[qemu_memorymap.h:#error]` Compile-time guard: Only one of PGTABLE_BASE_PADDR or PGTABLE_BASE_VADDR is defined

## Side Effects
- None

## Verification
- Run: `make test`
