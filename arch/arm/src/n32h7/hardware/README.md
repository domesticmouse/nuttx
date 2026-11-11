# hardware (`nuttx/arch/arm/src/n32h7/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/n32h7/hardware`, providing 23 header file(s) and 0 source file(s) (including `n32h76x_afio.h`, `n32h76x_dmamux.h`, `n32h76x_gpio.h`, `n32h76x_memorymap.h`).

## Interface
- `[n32h76x_afio.h:N32_AFIO_XSPI1_NON_OFFSET]`
- `[n32h76x_afio.h:N32_AFIO_EXTI_CFG_OFFSET]`
- `[n32h76x_afio.h:N32_AFIO_TOL5V_CFG0_2_OFFSET]`
- `[n32h76x_afio.h:N32_AFIO_TOL5V_CFG3_6_OFFSET]`
- `[n32h76x_afio.h:N32_AFIO_EFT_CFG_OFFSET]`
- `[n32h76x_afio.h:N32_AFIO_DIGEFT_CFG_OFFSET]`
- `[n32h76x_afio.h:N32_AFIO_SHRT1_EXEV_CFG_OFFSET]`
- `[n32h76x_afio.h:N32_AFIO_SHRT2_EXEV_CFG_OFFSET]`
- `[n32h76x_afio.h:N32_AFIO_SDRAM_HSMOD_CFG_OFFSET]`
- `[n32h76x_afio.h:N32_AFIO_SDRAM_VREF_EN_OFFSET]`
- `[n32h76x_afio.h:N32_AFIO_SDRAMDSN_CFG_OFFSET]`
- `[n32h76x_afio.h:N32_AFIO_SDRAMDSP_CFG_OFFSET]`
- `[n32h76x_dmamux.h:DMAMUX1_REQ_GEN0]`
- `[n32h76x_dmamux.h:DMAMUX1_REQ_GEN1]`
- `[n32h76x_dmamux.h:DMAMUX1_REQ_GEN2]`
- `[n32h76x_dmamux.h:DMAMUX1_REQ_GEN3]`
- `[n32h76x_dmamux.h:DMAMUX1_REQ_GEN4]`
- `[n32h76x_dmamux.h:DMAMUX1_REQ_GEN5]`
- `[n32h76x_dmamux.h:DMAMUX1_REQ_GEN6]`
- `[n32h76x_dmamux.h:DMAMUX1_REQ_GEN7]`
- `[n32h76x_dmamux.h:DMAMUX1_REQ_ADC1]`
- `[n32h76x_dmamux.h:DMAMUX1_REQ_ADC2]`
- `[n32h76x_dmamux.h:DMAMUX1_REQ_ADC3]`
- `[n32h76x_dmamux.h:DMAMUX1_REQ_SHRTIM1_DMA0]`
- `[n32h76x_gpio.h:N32_GPIO_MODER_OFFSET]`
- `[n32h76x_gpio.h:N32_GPIO_OTYPER_OFFSET]`
- `[n32h76x_gpio.h:N32_GPIO_SR_OFFSET]`
- `[n32h76x_gpio.h:N32_GPIO_PUPD_OFFSET]`
- `[n32h76x_gpio.h:N32_GPIO_PID_OFFSET]`
- `[n32h76x_gpio.h:N32_GPIO_POD_OFFSET]`

## Invariants
- `[n32h76x_memorymap.h:#error]` Compile-time guard: CONFIG_ARCH_CHIP_N32H7_CORTEXM7 not defined
- `[n32h7_afio.h:#error]` Compile-time guard: Unsupported N32 H7 part
- `[n32h7_dmamux.h:#error]` Compile-time guard: Unsupported N32 H7 part
- `[n32h7_gpio.h:#error]` Compile-time guard: Unsupported N32 H7 part
- `[n32h7_memorymap.h:#error]` Compile-time guard: Unsupported N32H7 memory map
- `[n32h7_pinmap.h:#error]` Compile-time guard: Unsupported N32H7 Pin map
- `[n32h7_pwr.h:#error]` Compile-time guard: Unsupported N32 H7 part
- `[n32h7_rcc.h:#error]` Compile-time guard: Unsupported STM32 H7 part
- `[n32h7_uart.h:#error]` Compile-time guard: Unsupported N32H7 memory map

## Side Effects
- None

## Verification
- Run: `make test`
