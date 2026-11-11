# hardware (`nuttx/arch/arm/src/stm32f0/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/stm32f0/hardware`, providing 13 header file(s) and 0 source file(s) (including `stm32_memorymap.h`, `stm32_pinmap.h`, `stm32_rcc.h`, `stm32f03x_memorymap.h`).

## Interface
- `[stm32_rcc.h:STM32_RCC_CR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_CFGR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_CIR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_APB2RSTR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_APB1RSTR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_AHBENR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_APB2ENR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_APB1ENR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_BDCR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_CSR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_AHBRSTR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_CFGR2_OFFSET]`
- `[stm32f03x_memorymap.h:STM32_CODE_BASE]`
- `[stm32f03x_memorymap.h:STM32_SRAM_BASE]`
- `[stm32f03x_memorymap.h:STM32_PERIPH_BASE]`
- `[stm32f03x_memorymap.h:STM32_CORTEX_BASE]`
- `[stm32f03x_memorymap.h:STM32_REGION_MASK]`
- `[stm32f03x_memorymap.h:STM32_IS_SRAM]`
- `[stm32f03x_memorymap.h:STM32_BOOT_BASE]`
- `[stm32f03x_memorymap.h:STM32_FLASH_BASE]`
- `[stm32f03x_memorymap.h:STM32_CCMRAM_BASE]`
- `[stm32f03x_memorymap.h:STM32_SYSMEM_BASE]`
- `[stm32f03x_memorymap.h:STM32_OPTION_BASE]`
- `[stm32f03x_memorymap.h:STM32_SYSMEM_UID]`
- `[stm32f03x_pinmap.h:GPIO_ADC1_IN0_0]`
- `[stm32f03x_pinmap.h:GPIO_ADC1_IN1_0]`
- `[stm32f03x_pinmap.h:GPIO_ADC1_IN2_0]`
- `[stm32f03x_pinmap.h:GPIO_ADC1_IN3_0]`
- `[stm32f03x_pinmap.h:GPIO_ADC1_IN4_0]`
- `[stm32f03x_pinmap.h:GPIO_ADC1_IN5_0]`

## Invariants
- `[stm32_memorymap.h:#error]` Compile-time guard: Unsupported STM32F0 memory map
- `[stm32_pinmap.h:#error]` Compile-time guard: Unsupported STM32F0 pin map

## Side Effects
- None

## Verification
- Run: `make test`
