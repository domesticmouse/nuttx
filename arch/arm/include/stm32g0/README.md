# stm32g0 (`nuttx/arch/arm/include/stm32g0`)

## Overview
Hardware abstraction and architecture package for `stm32g0` under `nuttx/arch/arm/include/stm32g0`, providing 2 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`).

## Interface
- `[chip.h:ARMV6M_PERIPHERAL_INTERRUPTS]`
- `[chip.h:STM32_FLASH_SIZE]`
- `[chip.h:STM32_SRAM_SIZE]`
- `[chip.h:STM32_NATIM]`
- `[chip.h:STM32_NGTIM16]`
- `[chip.h:STM32_NGTIM32]`
- `[chip.h:STM32_NBTIM]`
- `[chip.h:STM32_NSPI]`
- `[chip.h:STM32_NI2S]`
- `[chip.h:STM32_NI2C]`
- `[chip.h:STM32_NDMA]`
- `[chip.h:STM32_NUSART]`
- `[irq.h:STM32_IRQ_RESERVED]`
- `[irq.h:STM32_IRQ_NMI]`
- `[irq.h:STM32_IRQ_HARDFAULT]`
- `[irq.h:STM32_IRQ_SVCALL]`
- `[irq.h:STM32_IRQ_PENDSV]`
- `[irq.h:STM32_IRQ_SYSTICK]`
- `[irq.h:STM32_IRQ_EXTINT]`
- `[irq.h:STM32_IRQ_WWDG]`
- `[irq.h:STM32_IRQ_RESERVED1]`
- `[irq.h:STM32_IRQ_PVD]`
- `[irq.h:STM32_IRQ_RTC]`
- `[irq.h:STM32_IRQ_FLASH]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
