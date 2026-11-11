# phy62xx (`nuttx/arch/arm/include/phy62xx`)

## Overview
Hardware abstraction and architecture package for `phy62xx` under `nuttx/arch/arm/include/phy62xx`, providing 3 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`, `phy62xx_irq.h`).

## Interface
- `[chip.h:NVIC_SYSH_PRIORITY_MIN]`
- `[chip.h:NVIC_SYSH_PRIORITY_DEFAULT]`
- `[chip.h:NVIC_SYSH_PRIORITY_MAX]`
- `[chip.h:NVIC_SYSH_PRIORITY_STEP]`
- `[irq.h:PHY62XX_IRQ_RESERVED]`
- `[irq.h:PHY62XX_IRQ_NMI]`
- `[irq.h:PHY62XX_IRQ_HARDFAULT]`
- `[irq.h:PHY62XX_IRQ_SVCALL]`
- `[irq.h:PHY62XX_IRQ_PENDSV]`
- `[irq.h:PHY62XX_IRQ_SYSTICK]`
- `[irq.h:PHY62XX_IRQ_EXTINT]`
- `[irq.h:NR_IRQS]`
- `[phy62xx_irq.h:PHY62XX_IRQ_BB_IRQn]`
- `[phy62xx_irq.h:PHY62XX_IRQ_KSCAN_IRQn]`
- `[phy62xx_irq.h:PHY62XX_IRQ_RTC_IRQn]`
- `[phy62xx_irq.h:PHY62XX_IRQ_WDT_IRQn]`
- `[phy62xx_irq.h:PHY62XX_IRQ_UART0_IRQn]`
- `[phy62xx_irq.h:PHY62XX_IRQ_I2C0_IRQn]`
- `[phy62xx_irq.h:PHY62XX_IRQ_I2C1_IRQn]`
- `[phy62xx_irq.h:PHY62XX_IRQ_SPI0_IRQn]`
- `[phy62xx_irq.h:PHY62XX_IRQ_SPI1_IRQn]`
- `[phy62xx_irq.h:PHY62XX_IRQ_GPIO_IRQn]`
- `[phy62xx_irq.h:PHY62XX_IRQ_UART1_IRQn]`
- `[phy62xx_irq.h:PHY62XX_IRQ_SPIF_IRQn]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
