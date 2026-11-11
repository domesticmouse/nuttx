# fvp-v8r (`nuttx/arch/arm64/include/fvp-v8r`)

## Overview
Hardware abstraction and architecture package for `fvp-v8r` under `nuttx/arch/arm64/include/fvp-v8r`, providing 2 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`).

## Interface
- `[chip.h:KB]`
- `[chip.h:MB]`
- `[chip.h:GB]`
- `[chip.h:CONFIG_GICD_BASE]`
- `[chip.h:CONFIG_GICR_BASE]`
- `[chip.h:CONFIG_GICR_OFFSET]`
- `[chip.h:CONFIG_RAMBANK_ADDR]`
- `[chip.h:CONFIG_RAMBANK_SIZE]`
- `[chip.h:CONFIG_RAMBANK_END]`
- `[chip.h:CONFIG_DEVICEIO1_BASEADDR]`
- `[irq.h:NR_IRQS]`
- `[irq.h:MPID_TO_CORE]`

## Invariants
- `[chip.h:#error]` Compile-time guard: CONFIG_ARM64_GIC_VERSION should be 2, 3 or 4

## Side Effects
- None

## Verification
- Run: `make test`
