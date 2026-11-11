# zynq-mpsoc (`nuttx/arch/arm64/include/zynq-mpsoc`)

## Overview
Hardware abstraction and architecture package for `zynq-mpsoc` under `nuttx/arch/arm64/include/zynq-mpsoc`, providing 2 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`).

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
- `[irq.h:ZYNQ_MPSOC_IRQ_RPU0_PERF_MON]`
- `[irq.h:ZYNQ_MPSOC_IRQ_RPU1_PERF_MON]`
- `[irq.h:ZYNQ_MPSOC_IRQ_OCM_ECC_ERROR]`
- `[irq.h:ZYNQ_MPSOC_IRQ_LPD_APB_ERROR]`
- `[irq.h:ZYNQ_MPSOC_IRQ_RPU0_ECC_ERROR]`
- `[irq.h:ZYNQ_MPSOC_IRQ_RPU1_ECC_ERROR]`
- `[irq.h:ZYNQ_MPSOC_IRQ_NAND]`
- `[irq.h:ZYNQ_MPSOC_IRQ_QSPI]`
- `[irq.h:ZYNQ_MPSOC_IRQ_GPIO]`
- `[irq.h:ZYNQ_MPSOC_IRQ_I2C0]`
- `[irq.h:ZYNQ_MPSOC_IRQ_I2C1]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
