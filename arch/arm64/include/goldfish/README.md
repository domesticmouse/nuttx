# goldfish (`nuttx/arch/arm64/include/goldfish`)

## Overview
Hardware abstraction and architecture package for `goldfish` under `nuttx/arch/arm64/include/goldfish`, providing 2 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`).

## Interface
- `[chip.h:KB]`
- `[chip.h:MB]`
- `[chip.h:GB]`
- `[chip.h:CONFIG_GICD_BASE]`
- `[chip.h:CONFIG_GICR_BASE]`
- `[chip.h:CONFIG_GICR_OFFSET]`
- `[chip.h:CONFIG_FLASH_BASEADDR]`
- `[chip.h:CONFIG_FLASH_SIZE]`
- `[chip.h:CONFIG_DEVICEIO_BASEADDR]`
- `[chip.h:CONFIG_DEVICEIO_SIZE]`
- `[irq.h:NR_IRQS]`
- `[irq.h:MPID_TO_CORE]`

## Invariants
- `[chip.h:#error]` Compile-time guard: CONFIG_ARM64_GIC_VERSION should be 2, 3 or 4

## Side Effects
- None

## Verification
- Run: `make test`
