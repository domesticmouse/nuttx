# rk3588 (`nuttx/arch/arm64/include/rk3588`)

## Overview
Hardware abstraction and architecture package for `rk3588` under `nuttx/arch/arm64/include/rk3588`, providing 2 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`).

## Interface
- `[chip.h:CONFIG_GICD_BASE]`
- `[chip.h:CONFIG_GICD_SIZE]`
- `[chip.h:CONFIG_GICR_BASE]`
- `[chip.h:CONFIG_GICR_SIZE]`
- `[chip.h:CONFIG_GICR_OFFSET]`
- `[chip.h:CONFIG_RAMBANK1_ADDR]`
- `[chip.h:CONFIG_RAMBANK1_SIZE]`
- `[chip.h:RK3588_UART_MMU_SIZE]`
- `[chip.h:CONFIG_LOAD_BASE]`
- `[chip.h:MPID_TO_CLUSTER_ID]`
- `[irq.h:NR_IRQS]`
- `[irq.h:RK3588_IRQ_UART2]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
