# hardware (`nuttx/arch/arm/src/stm32l5/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/stm32l5/hardware`, providing 9 header file(s) and 0 source file(s) (including `stm32_rcc.h`, `stm32l562xx_pinmap.h`, `stm32l562xx_syscfg.h`, `stm32l5_flash.h`).

## Interface
- `[stm32_rcc.h:STM32_RCC_CR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_ICSCR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_CFGR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_PLLCFG_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_PLLSAI1CFG_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_PLLSAI2CFG_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_CIER_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_CIFR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_CICR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_AHB1RSTR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_AHB2RSTR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_AHB3RSTR_OFFSET]`
- `[stm32l562xx_pinmap.h:GPIO_ADC12_IN1_0]`
- `[stm32l562xx_pinmap.h:GPIO_ADC12_IN2_0]`
- `[stm32l562xx_pinmap.h:GPIO_ADC12_IN3_0]`
- `[stm32l562xx_pinmap.h:GPIO_ADC12_IN4_0]`
- `[stm32l562xx_pinmap.h:GPIO_ADC12_IN5_0]`
- `[stm32l562xx_pinmap.h:GPIO_ADC12_IN6_0]`
- `[stm32l562xx_pinmap.h:GPIO_ADC12_IN7_0]`
- `[stm32l562xx_pinmap.h:GPIO_ADC12_IN8_0]`
- `[stm32l562xx_pinmap.h:GPIO_ADC12_IN9_0]`
- `[stm32l562xx_pinmap.h:GPIO_ADC12_IN10_0]`
- `[stm32l562xx_pinmap.h:GPIO_ADC12_IN11_0]`
- `[stm32l562xx_pinmap.h:GPIO_ADC12_IN12_0]`
- `[stm32l562xx_syscfg.h:STM32_SYSCFG_SECCFGR_OFFSET]`
- `[stm32l562xx_syscfg.h:STM32_SYSCFG_CFGR1_OFFSET]`
- `[stm32l562xx_syscfg.h:STM32_SYSCFG_FPUIMR_OFFSET]`
- `[stm32l562xx_syscfg.h:STM32_SYSCFG_CNSLCKR_OFFSET]`
- `[stm32l562xx_syscfg.h:STM32_SYSCFG_CSLCKR_OFFSET]`
- `[stm32l562xx_syscfg.h:STM32_SYSCFG_CFGR2_OFFSET]`

## Invariants
- `[stm32l5_flash.h:#error]` Compile-time guard: unknown flash configuration!
- `[stm32l5_pinmap.h:#error]` Compile-time guard: Unsupported STM32 L5 pin map
- `[stm32l5_spi.h:#error]` Compile-time guard: Unsupported STM32 L5 chip
- `[stm32l5_syscfg.h:#error]` Compile-time guard: Unsupported STM32 L5 chip

## Side Effects
- None

## Verification
- Run: `make test`
