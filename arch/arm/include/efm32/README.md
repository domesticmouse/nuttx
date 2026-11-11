# efm32 (`nuttx/arch/arm/include/efm32`)

## Overview
Hardware abstraction and architecture package for `efm32` under `nuttx/arch/arm/include/efm32`, providing 5 header file(s) and 0 source file(s) (including `chip.h`, `efm32g_irq.h`, `efm32gg_irq.h`, `efm32tg_irq.h`).

## Interface
- `[chip.h:NVIC_SYSH_PRIORITY_MIN]`
- `[chip.h:NVIC_SYSH_PRIORITY_DEFAULT]`
- `[chip.h:NVIC_SYSH_PRIORITY_MAX]`
- `[chip.h:NVIC_SYSH_PRIORITY_STEP]`
- `[efm32g_irq.h:EFM32_IRQ_DMA]`
- `[efm32g_irq.h:EFM32_IRQ_GPIO_EVEN]`
- `[efm32g_irq.h:EFM32_IRQ_TIMER0]`
- `[efm32g_irq.h:EFM32_IRQ_USART0_RX]`
- `[efm32g_irq.h:EFM32_IRQ_USART0_TX]`
- `[efm32g_irq.h:EFM32_IRQ_ACMP]`
- `[efm32g_irq.h:EFM32_IRQ_ADC0]`
- `[efm32g_irq.h:EFM32_IRQ_DAC0]`
- `[efm32g_irq.h:EFM32_IRQ_I2C0]`
- `[efm32g_irq.h:EFM32_IRQ_GPIO_ODD]`
- `[efm32g_irq.h:EFM32_IRQ_TIMER1]`
- `[efm32g_irq.h:EFM32_IRQ_TIMER2]`
- `[efm32gg_irq.h:EFM32_IRQ_DMA]`
- `[efm32gg_irq.h:EFM32_IRQ_GPIO_EVEN]`
- `[efm32gg_irq.h:EFM32_IRQ_TIMER0]`
- `[efm32gg_irq.h:EFM32_IRQ_USART0_RX]`
- `[efm32gg_irq.h:EFM32_IRQ_USART0_TX]`
- `[efm32gg_irq.h:EFM32_IRQ_USB]`
- `[efm32gg_irq.h:EFM32_IRQ_ACMP]`
- `[efm32gg_irq.h:EFM32_IRQ_ADC0]`
- `[efm32gg_irq.h:EFM32_IRQ_DAC0]`
- `[efm32gg_irq.h:EFM32_IRQ_I2C0]`
- `[efm32gg_irq.h:EFM32_IRQ_I2C1]`
- `[efm32gg_irq.h:EFM32_IRQ_GPIO_ODD]`
- `[efm32tg_irq.h:EFM32_IRQ_DMA]`
- `[efm32tg_irq.h:EFM32_IRQ_GPIO_EVEN]`

## Invariants
- `[chip.h:#error]` Compile-time guard: Unsupported EFM32 chip
- `[irq.h:#error]` Compile-time guard: Unsupported EFM32 chip

## Side Effects
- None

## Verification
- Run: `make test`
