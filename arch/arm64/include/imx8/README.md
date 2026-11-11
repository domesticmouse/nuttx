# imx8 (`nuttx/arch/arm64/include/imx8`)

## Overview
Hardware abstraction and architecture package for `imx8` under `nuttx/arch/arm64/include/imx8`, providing 2 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`).

## Interface
- `[chip.h:KB]`
- `[chip.h:MB]`
- `[chip.h:GB]`
- `[chip.h:CONFIG_GICD_BASE]`
- `[chip.h:CONFIG_GICR_BASE]`
- `[chip.h:CONFIG_GICR_OFFSET]`
- `[chip.h:CONFIG_RAMBANK1_ADDR]`
- `[chip.h:CONFIG_RAMBANK1_SIZE]`
- `[chip.h:CONFIG_DEVICEIO_BASEADDR]`
- `[chip.h:CONFIG_DEVICEIO_SIZE]`
- `[chip.h:CONFIG_LOAD_BASE]`
- `[chip.h:MPID_TO_CLUSTER_ID]`
- `[irq.h:NR_IRQS]`

## Invariants
- `[chip.h:#error]` Compile-time guard: CONFIG_ARM64_GIC_VERSION should be 2, 3 or 4

## Side Effects
- None

## Verification
- Run: `make test`
