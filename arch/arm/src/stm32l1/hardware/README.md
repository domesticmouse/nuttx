# hardware (`nuttx/arch/arm/src/stm32l1/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/stm32l1/hardware`, providing 8 header file(s) and 0 source file(s) (including `stm32_memorymap.h`, `stm32_pinmap.h`, `stm32_rcc.h`, `stm32l15xxx_aes.h`).

## Interface
- `[stm32_rcc.h:STM32_RCC_CR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_ICSCR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_CFGR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_CIR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_AHBRSTR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_APB2RSTR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_APB1RSTR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_AHBENR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_APB2ENR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_APB1ENR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_AHBLPENR_OFFSET]`
- `[stm32_rcc.h:STM32_RCC_APB2LPENR_OFFSET]`
- `[stm32l15xxx_aes.h:STM32_AES_CR_OFFSET]`
- `[stm32l15xxx_aes.h:STM32_AES_SR_OFFSET]`
- `[stm32l15xxx_aes.h:STM32_AES_DINR_OFFSET]`
- `[stm32l15xxx_aes.h:STM32_AES_DOUTR_OFFSET]`
- `[stm32l15xxx_aes.h:STM32_AES_KEYR0_OFFSET]`
- `[stm32l15xxx_aes.h:STM32_AES_KEYR1_OFFSET]`
- `[stm32l15xxx_aes.h:STM32_AES_KEYR2_OFFSET]`
- `[stm32l15xxx_aes.h:STM32_AES_KEYR3_OFFSET]`
- `[stm32l15xxx_aes.h:STM32_AES_IVR0_OFFSET]`
- `[stm32l15xxx_aes.h:STM32_AES_IVR1_OFFSET]`
- `[stm32l15xxx_aes.h:STM32_AES_IVR2_OFFSET]`
- `[stm32l15xxx_aes.h:STM32_AES_IVR3_OFFSET]`
- `[stm32l15xxx_gpio.h:STM32_NGPIO_PORTS]`
- `[stm32l15xxx_gpio.h:STM32_GPIO_MODER_OFFSET]`
- `[stm32l15xxx_gpio.h:STM32_GPIO_OTYPER_OFFSET]`
- `[stm32l15xxx_gpio.h:STM32_GPIO_OSPEED_OFFSET]`
- `[stm32l15xxx_gpio.h:STM32_GPIO_PUPDR_OFFSET]`
- `[stm32l15xxx_gpio.h:STM32_GPIO_IDR_OFFSET]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
