# s698pm (`nuttx/arch/sparc/include/s698pm`)

## Overview
Hardware abstraction and architecture package for `s698pm` under `nuttx/arch/sparc/include/s698pm`, providing 1 header file(s) and 0 source file(s) (including `irq.h`).

## Interface
- `[irq.h:S698PM_IRQREG_BASE]`
- `[irq.h:S698PM_IRQREG_ILEVEL]`
- `[irq.h:S698PM_IRQREG_IPEND]`
- `[irq.h:S698PM_IRQREG_IFORCE]`
- `[irq.h:S698PM_IRQREG_ICLEAR]`
- `[irq.h:S698PM_IRQREG_MPSTATUS]`
- `[irq.h:S698PM_IRQREG_BROADCAST]`
- `[irq.h:S698PM_IRQREG_P0_MASK]`
- `[irq.h:S698PM_IRQREG_P1_MASK]`
- `[irq.h:S698PM_IRQREG_P2_MASK]`
- `[irq.h:S698PM_IRQREG_P3_MASK]`
- `[irq.h:S698PM_IRQREG_P0_FORCE]`

## Invariants
- `[irq.h:#error]` Compile-time guard: Unrecognized chip

## Side Effects
- None

## Verification
- Run: `make test`
