# bcm2711 (`nuttx/arch/arm64/include/bcm2711`)

## Overview
Hardware abstraction and architecture package for `bcm2711` under `nuttx/arch/arm64/include/bcm2711`, providing 2 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`).

## Interface
- `[chip.h:KB]`
- `[chip.h:MB]`
- `[chip.h:GB]`
- `[chip.h:BCM_GIC400_BASEADDR]`
- `[chip.h:BCM_GIC400_DISTOFFSET]`
- `[chip.h:BCM_GIC400_RDISTOFFSET]`
- `[chip.h:CONFIG_GICD_BASE]`
- `[chip.h:CONFIG_GICR_BASE]`
- `[chip.h:CONFIG_GICR_OFFSET]`
- `[chip.h:CONFIG_RAMBANK1_ADDR]`
- `[chip.h:CONFIG_RAMBANK1_SIZE]`
- `[irq.h:NR_IRQS]`
- `[irq.h:MPID_TO_CORE]`
- `[irq.h:BCM_IRQ_ARMC_BASE]`
- `[irq.h:BCM_IRQ_ARMC]`
- `[irq.h:BCM_IRQ_ARMC_TIMER]`
- `[irq.h:BCM_IRQ_ARMC_MAILBOX]`
- `[irq.h:BCM_IRQ_ARMC_DOORBELL0]`
- `[irq.h:BCM_IRQ_ARMC_DOORBELL1]`
- `[irq.h:BCM_IRQ_ARMC_VPU0HALT]`
- `[irq.h:BCM_IRQ_ARMC_VPU1HALT]`
- `[irq.h:BCM_IRQ_ARMC_ARMADDRERR]`
- `[irq.h:BCM_IRQ_ARMC_ARMAXIERR]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
