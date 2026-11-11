# hardware (`nuttx/arch/arm/src/stm32f2/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/stm32f2/hardware`, providing 7 header file(s) and 0 source file(s) (including `stm32_memorymap.h`, `stm32_pinmap.h`, `stm32_rcc.h`, `stm32f20xxx_gpio.h`).

## Interface
- `[stm32_rcc.h:STM32_RCC_CR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_PLLCFG_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_CFGR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_CIR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_AHB1RSTR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_AHB2RSTR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_AHB3RSTR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_APB1RSTR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_APB2RSTR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_AHB1ENR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_AHB2ENR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_AHB3ENR_OFFSET]`
- `[stm32f20xxx_gpio.h:STM32_NGPIO_PORTS]`
- `[stm32f20xxx_gpio.h:STM32_GPIO_MODER_OFFSET]`
- `[stm32f20xxx_gpio.h:STM32_GPIO_OTYPER_OFFSET]`
- `[stm32f20xxx_gpio.h:STM32_GPIO_OSPEED_OFFSET]`
- `[stm32f20xxx_gpio.h:STM32_GPIO_PUPDR_OFFSET]`
- `[stm32f20xxx_gpio.h:STM32_GPIO_IDR_OFFSET]`
- `[stm32f20xxx_gpio.h:STM32_GPIO_ODR_OFFSET]`
- `[stm32f20xxx_gpio.h:STM32_GPIO_BSRR_OFFSET]`
- `[stm32f20xxx_gpio.h:STM32_GPIO_LCKR_OFFSET]`
- `[stm32f20xxx_gpio.h:STM32_GPIO_AFRL_OFFSET]`
- `[stm32f20xxx_gpio.h:STM32_GPIO_AFRH_OFFSET]`
- `[stm32f20xxx_gpio.h:STM32_GPIOA_MODER]`
- `[stm32f20xxx_memorymap.h:STM32_CODE_BASE]`
- `[stm32f20xxx_memorymap.h:STM32_SRAM_BASE]`
- `[stm32f20xxx_memorymap.h:STM32_PERIPH_BASE]`
- `[stm32f20xxx_memorymap.h:STM32_FSMC_BASE12]`
- `[stm32f20xxx_memorymap.h:STM32_FSMC_BANK1]`
- `[stm32f20xxx_memorymap.h:STM32_FSMC_BANK2]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
