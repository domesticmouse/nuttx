# hardware (`nuttx/arch/arm/src/stm32wl5/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/stm32wl5/hardware`, providing 11 header file(s) and 0 source file(s) (including `stm32_rcc.h`, `stm32wl5_exti.h`, `stm32wl5_flash.h`, `stm32wl5_gpio.h`).

## Interface
- `[stm32_rcc.h:STM32_RCC_CR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_ICSCR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_CFGR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_PLLCFG_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_CIER_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_CIFR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_CICR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_AHB1RSTR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_AHB2RSTR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_AHB3RSTR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_APB1RSTR1_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_APB1RSTR2_OFFSET]`
- `[stm32wl5_exti.h:STM32_NEXTI1]`
- `[stm32wl5_exti.h:STM32_EXTI1_MASK]`
- `[stm32wl5_exti.h:STM32_NEXTI2]`
- `[stm32wl5_exti.h:STM32_EXTI2_MASK]`
- `[stm32wl5_exti.h:STM32_EXTI_RTSR1_OFFSET]`
- `[stm32wl5_exti.h:STM32_EXTI_FTSR1_OFFSET]`
- `[stm32wl5_exti.h:STM32_EXTI_SWIER1_OFFSET]`
- `[stm32wl5_exti.h:STM32_EXTI_PR1_OFFSET]`
- `[stm32wl5_exti.h:STM32_EXTI_RTSR2_OFFSET]`
- `[stm32wl5_exti.h:STM32_EXTI_FTSR2_OFFSET]`
- `[stm32wl5_exti.h:STM32_EXTI_SWIER2_OFFSET]`
- `[stm32wl5_exti.h:STM32_EXTI_PR2_OFFSET]`
- `[stm32wl5_flash.h:CONFIG_STM32_FLASH_OVERRIDE_E]`
- `[stm32wl5_flash.h:CONFIG_STM32_FLASH_CONFIG_8]`
- `[stm32wl5_flash.h:CONFIG_STM32_FLASH_CONFIG_B]`
- `[stm32wl5_flash.h:CONFIG_STM32_FLASH_CONFIG_C]`
- `[stm32wl5_flash.h:CONFIG_STM32_FLASH_CONFIG_E]`
- `[stm32wl5_flash.h:CONFIG_STM32_FLASH_CONFIG_G]`

## Invariants
- `[stm32wl5_flash.h:#error]` Compile-time guard: unknown flash configuration!

## Side Effects
- None

## Verification
- Run: `make test`
