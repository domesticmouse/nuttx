# a527 (`nuttx/arch/arm64/include/a527`)

## Overview
Hardware abstraction and architecture package for `a527` under `nuttx/arch/arm64/include/a527`, providing 2 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`).

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
- `[irq.h:MPID_TO_CORE]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
