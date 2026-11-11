# imx9 (`nuttx/arch/arm/include/imx9`)

## Overview
Hardware abstraction and architecture package for `imx9` under `nuttx/arch/arm/include/imx9`, providing 4 header file(s) and 0 source file(s) (including `chip.h`, `imx93_irq.h`, `imx95_irq.h`, `irq.h`).

## Interface
- `[chip.h:NVIC_SYSH_PRIORITY_MIN]`
- `[chip.h:NVIC_SYSH_PRIORITY_DEFAULT]`
- `[chip.h:NVIC_SYSH_PRIORITY_MAX]`
- `[chip.h:NVIC_SYSH_PRIORITY_STEP]`
- `[chip.h:IMX9_GPIO_NPORTS]`
- `[imx93_irq.h:IMX9_IRQ_RESERVED32]`
- `[imx93_irq.h:IMX9_IRQ_RESERVED33]`
- `[imx93_irq.h:IMX9_IRQ_RESERVED34]`
- `[imx93_irq.h:IMX9_IRQ_RESERVED35]`
- `[imx93_irq.h:IMX9_IRQ_RESERVED36]`
- `[imx93_irq.h:IMX9_IRQ_RESERVED37]`
- `[imx93_irq.h:IMX9_IRQ_RESERVED38]`
- `[imx93_irq.h:IMX9_IRQ_RESERVED39]`
- `[imx93_irq.h:IMX9_IRQ_CAN1]`
- `[imx93_irq.h:IMX9_IRQ_CAN1_ERROR]`
- `[imx93_irq.h:IMX9_IRQ_GPIO1_0]`
- `[imx93_irq.h:IMX9_IRQ_GPIO1_1]`
- `[imx95_irq.h:IMX9_IRQ_RESERVED16]`
- `[imx95_irq.h:IMX9_IRQ_RESERVED17]`
- `[imx95_irq.h:IMX9_IRQ_RESERVED18]`
- `[imx95_irq.h:IMX9_IRQ_RESERVED19]`
- `[imx95_irq.h:IMX9_IRQ_RESERVED20]`
- `[imx95_irq.h:IMX9_IRQ_RESERVED21]`
- `[imx95_irq.h:IMX9_IRQ_RESERVED22]`
- `[imx95_irq.h:IMX9_IRQ_RESERVED23]`
- `[imx95_irq.h:IMX9_IRQ_CAN1]`
- `[imx95_irq.h:IMX9_IRQ_CAN1_ERROR]`
- `[imx95_irq.h:IMX9_IRQ_GPIO1_0]`
- `[imx95_irq.h:IMX9_IRQ_GPIO1_1]`
- `[irq.h:IMX9_IRQ_RESERVED]`

## Invariants
- `[irq.h:#error]` Compile-time guard: Unrecognized i.MX9 architecture

## Side Effects
- None

## Verification
- Run: `make test`
