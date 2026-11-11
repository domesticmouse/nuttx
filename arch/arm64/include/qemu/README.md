# qemu (`nuttx/arch/arm64/include/qemu`)

## Overview
Hardware abstraction and architecture package for `qemu` under `nuttx/arch/arm64/include/qemu`, providing 2 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`).

## Interface
- `[chip.h:KB]`
- `[chip.h:MB]`
- `[chip.h:GB]`
- `[chip.h:CONFIG_GICD_BASE]`
- `[chip.h:CONFIG_GICR_BASE]`
- `[chip.h:CONFIG_GICM_BASE]`
- `[chip.h:CONFIG_GICR_OFFSET]`
- `[chip.h:CONFIG_RAMBANK1_ADDR]`
- `[chip.h:CONFIG_RAMBANK1_SIZE]`
- `[chip.h:CONFIG_DEVICEIO_BASEADDR]`
- `[irq.h:NR_IRQS]`
- `[irq.h:MPID_TO_CORE]`

## Invariants
- `[chip.h:#error]` Compile-time guard: CONFIG_ARM64_GIC_VERSION should be 2, 3 or 4

## Side Effects
- None

## Verification
- Run: `make test`
