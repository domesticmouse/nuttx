# hardware (`nuttx/arch/arm/src/stm32l0/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/stm32l0/hardware`, providing 9 header file(s) and 0 source file(s) (including `stm32_memorymap.h`, `stm32_pinmap.h`, `stm32_rcc.h`, `stm32l0_exti.h`).

## Interface
- `[stm32_rcc.h:STM32_RCC_CR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_ICSCR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_CRRCR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_CFGR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_CIER_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_CIFR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_CICR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_IOPRSTR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_AHBRSTR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_APB2RSTR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_APB1RSTR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_IOPENR_OFFSET]`
- `[stm32l0_exti.h:STM32_NEXTI]`
- `[stm32l0_exti.h:STM32_EXTI_MASK]`
- `[stm32l0_exti.h:STM32_EXTI_BIT]`
- `[stm32l0_exti.h:STM32_EXTI_IMR_OFFSET]`
- `[stm32l0_exti.h:STM32_EXTI_EMR_OFFSET]`
- `[stm32l0_exti.h:STM32_EXTI_RTSR_OFFSET]`
- `[stm32l0_exti.h:STM32_EXTI_FTSR_OFFSET]`
- `[stm32l0_exti.h:STM32_EXTI_SWIER_OFFSET]`
- `[stm32l0_exti.h:STM32_EXTI_PR_OFFSET]`
- `[stm32l0_exti.h:STM32_EXTI_IMR]`
- `[stm32l0_exti.h:STM32_EXTI_EMR]`
- `[stm32l0_exti.h:STM32_EXTI_RTSR]`
- `[stm32l0_flash.h:STM32_FLASH_ACR_OFFSET]`
- `[stm32l0_flash.h:STM32_FLASH_PECR_OFFSET]`
- `[stm32l0_flash.h:STM32_FLASH_PDKEYR_OFFSET]`
- `[stm32l0_flash.h:STM32_FLASH_PEKEYR_OFFSET]`
- `[stm32l0_flash.h:STM32_FLASH_PRGKEYR_OFFSET]`
- `[stm32l0_flash.h:STM32_FLASH_OPTKEYR_OFFSET]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
