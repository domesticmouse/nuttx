# hardware (`nuttx/arch/risc-v/src/sg2000/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/risc-v/src/sg2000/hardware`, providing 2 header file(s) and 0 source file(s) (including `sg2000_memorymap.h`, `sg2000_plic.h`).

## Interface
- `[sg2000_memorymap.h:SG2000_PLIC_BASE]`
- `[sg2000_plic.h:SG2000_PLIC_PRIORITY]`
- `[sg2000_plic.h:SG2000_PLIC_ENABLE1]`
- `[sg2000_plic.h:SG2000_PLIC_ENABLE2]`
- `[sg2000_plic.h:SG2000_PLIC_THRESHOLD]`
- `[sg2000_plic.h:SG2000_PLIC_CLAIM]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
