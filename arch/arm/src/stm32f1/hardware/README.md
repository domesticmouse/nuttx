# hardware (`nuttx/arch/arm/src/stm32f1/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/stm32f1/hardware`, providing 14 header file(s) and 0 source file(s) (including `stm32_memorymap.h`, `stm32_pinmap.h`, `stm32_rcc.h`, `stm32f100_pinmap.h`).

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
- `[stm32f100_pinmap.h:GPIO_ADC1_IN0_0]`
- `[stm32f100_pinmap.h:GPIO_ADC1_IN1_0]`
- `[stm32f100_pinmap.h:GPIO_ADC1_IN2_0]`
- `[stm32f100_pinmap.h:GPIO_ADC1_IN3_0]`
- `[stm32f100_pinmap.h:GPIO_ADC1_IN4_0]`
- `[stm32f100_pinmap.h:GPIO_ADC1_IN5_0]`
- `[stm32f100_pinmap.h:GPIO_ADC1_IN6_0]`
- `[stm32f100_pinmap.h:GPIO_ADC1_IN7_0]`
- `[stm32f100_pinmap.h:GPIO_ADC1_IN8_0]`
- `[stm32f100_pinmap.h:GPIO_ADC1_IN9_0]`
- `[stm32f100_pinmap.h:GPIO_ADC1_IN10_0]`
- `[stm32f100_pinmap.h:GPIO_ADC1_IN11_0]`
- `[stm32f102_pinmap.h:GPIO_ADC12_IN0_0]`
- `[stm32f102_pinmap.h:GPIO_ADC12_IN1_0]`
- `[stm32f102_pinmap.h:GPIO_ADC12_IN2_0]`
- `[stm32f102_pinmap.h:GPIO_ADC12_IN3_0]`
- `[stm32f102_pinmap.h:GPIO_ADC12_IN4_0]`
- `[stm32f102_pinmap.h:GPIO_ADC12_IN5_0]`

## Invariants
- `[stm32_pinmap.h:#error]` Compile-time guard: Unsupported STM32F1 pin map
- `[stm32f103c_pinmap.h:#error]` Compile-time guard: CAN1_REMAP2 not supported on this architecture

## Side Effects
- None

## Verification
- Run: `make test`
