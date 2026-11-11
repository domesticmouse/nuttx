# hardware (`nuttx/arch/arm/src/stm32g4/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/stm32g4/hardware`, providing 21 header file(s) and 0 source file(s) (including `stm32_memorymap.h`, `stm32_pinmap.h`, `stm32_rcc.h`, `stm32g47xxx_hrtim.h`).

## Interface
- `[stm32_rcc.h:STM32_RCC_CR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_ICSCR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_CFGR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_PLLCFGR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_CIER_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_CIFR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_CICR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_AHB1RSTR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_AHB2RSTR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_AHB3RSTR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_APB1RSTR1_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_APB1RSTR2_OFFSET]`
- `[stm32g47xxx_hrtim.h:STM32_HRTIM_MASTER_OFFSET]`
- `[stm32g47xxx_hrtim.h:STM32_HRTIM_TIMERA_OFFSET]`
- `[stm32g47xxx_hrtim.h:STM32_HRTIM_TIMERB_OFFSET]`
- `[stm32g47xxx_hrtim.h:STM32_HRTIM_TIMERC_OFFSET]`
- `[stm32g47xxx_hrtim.h:STM32_HRTIM_TIMERD_OFFSET]`
- `[stm32g47xxx_hrtim.h:STM32_HRTIM_TIMERE_OFFSET]`
- `[stm32g47xxx_hrtim.h:STM32_HRTIM_TIMERF_OFFSET]`
- `[stm32g47xxx_hrtim.h:STM32_HRTIM_CMN_OFFSET]`
- `[stm32g47xxx_hrtim.h:STM32_HRTIM1_MASTER_BASE]`
- `[stm32g47xxx_hrtim.h:STM32_HRTIM1_TIMERA_BASE]`
- `[stm32g47xxx_hrtim.h:STM32_HRTIM1_TIMERB_BASE]`
- `[stm32g47xxx_hrtim.h:STM32_HRTIM1_TIMERC_BASE]`
- `[stm32g4xxc_pinmap.h:GPIO_ADC1_IN1_0]`
- `[stm32g4xxc_pinmap.h:GPIO_ADC1_IN2_0]`
- `[stm32g4xxc_pinmap.h:GPIO_ADC1_IN3_0]`
- `[stm32g4xxc_pinmap.h:GPIO_ADC1_IN4_0]`
- `[stm32g4xxc_pinmap.h:GPIO_ADC1_IN5_0]`
- `[stm32g4xxc_pinmap.h:GPIO_ADC1_IN10_0]`

## Invariants
- `[stm32g4xxp_pinmap.h:#error]` Compile-time guard: missing pinmap for STM32G4XXP
- `[stm32g4xxxx_pinmap.h:#error]` Compile-time guard: Unknown STM32G4xxxx chip!

## Side Effects
- None

## Verification
- Run: `make test`
