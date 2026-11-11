# hardware (`nuttx/arch/arm/src/stm32f3/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/stm32f3/hardware`, providing 20 header file(s) and 0 source file(s) (including `stm32_memorymap.h`, `stm32_pinmap.h`, `stm32_rcc.h`, `stm32f30xxx_gpio.h`).

## Interface
- `[stm32f30xxx_gpio.h:STM32_NGPIO_PORTS]`
- `[stm32f30xxx_gpio.h:STM32_GPIO_MODER_OFFSET]`
- `[stm32f30xxx_gpio.h:STM32_GPIO_OTYPER_OFFSET]`
- `[stm32f30xxx_gpio.h:STM32_GPIO_OSPEED_OFFSET]`
- `[stm32f30xxx_gpio.h:STM32_GPIO_PUPDR_OFFSET]`
- `[stm32f30xxx_gpio.h:STM32_GPIO_IDR_OFFSET]`
- `[stm32f30xxx_gpio.h:STM32_GPIO_ODR_OFFSET]`
- `[stm32f30xxx_gpio.h:STM32_GPIO_BSRR_OFFSET]`
- `[stm32f30xxx_gpio.h:STM32_GPIO_LCKR_OFFSET]`
- `[stm32f30xxx_gpio.h:STM32_GPIO_AFRL_OFFSET]`
- `[stm32f30xxx_gpio.h:STM32_GPIO_AFRH_OFFSET]`
- `[stm32f30xxx_gpio.h:STM32_GPIO_BRR_OFFSET]`
- `[stm32f30xxx_memorymap.h:STM32_CODE_BASE]`
- `[stm32f30xxx_memorymap.h:STM32_SRAM_BASE]`
- `[stm32f30xxx_memorymap.h:STM32_PERIPH_BASE]`
- `[stm32f30xxx_memorymap.h:STM32_CORTEX_BASE]`
- `[stm32f30xxx_memorymap.h:STM32_REGION_MASK]`
- `[stm32f30xxx_memorymap.h:STM32_IS_SRAM]`
- `[stm32f30xxx_memorymap.h:STM32_BOOT_BASE]`
- `[stm32f30xxx_memorymap.h:STM32_FLASH_BASE]`
- `[stm32f30xxx_memorymap.h:STM32_CCMRAM_BASE]`
- `[stm32f30xxx_memorymap.h:STM32_SYSMEM_BASE]`
- `[stm32f30xxx_memorymap.h:STM32_OPTION_BASE]`
- `[stm32f30xxx_memorymap.h:STM32_SYSMEM_UID]`
- `[stm32f30xxx_pinmap.h:GPIO_ADC1_IN1_0]`
- `[stm32f30xxx_pinmap.h:GPIO_ADC1_IN2_0]`
- `[stm32f30xxx_pinmap.h:GPIO_ADC1_IN3_0]`
- `[stm32f30xxx_pinmap.h:GPIO_ADC1_IN4_0]`
- `[stm32f30xxx_pinmap.h:GPIO_ADC1_IN5_0]`
- `[stm32f30xxx_pinmap.h:GPIO_ADC1_IN6_0]`

## Invariants
- `[stm32_memorymap.h:#error]` Compile-time guard: Unsupported STM32F3 memory map
- `[stm32_pinmap.h:#error]` Compile-time guard: Unsupported STM32F3 pin map
- `[stm32_rcc.h:#error]` Compile-time guard: Unsupported STM32 F3 part

## Side Effects
- None

## Verification
- Run: `make test`
