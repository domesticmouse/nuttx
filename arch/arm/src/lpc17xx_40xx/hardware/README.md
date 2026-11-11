# hardware (`nuttx/arch/arm/src/lpc17xx_40xx/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/lpc17xx_40xx/hardware`, providing 36 header file(s) and 0 source file(s) (including `lpc176x_memorymap.h`, `lpc176x_pinconfig.h`, `lpc176x_pinconn.h`, `lpc176x_syscon.h`).

## Interface
- `[lpc176x_memorymap.h:LPC17_40_FLASH_BASE]`
- `[lpc176x_memorymap.h:LPC17_40_SRAM_BASE]`
- `[lpc176x_memorymap.h:LPC17_40_ROM_BASE]`
- `[lpc176x_memorymap.h:LPC17_40_AHBSRAM_BASE]`
- `[lpc176x_memorymap.h:LPC17_40_SRAM_BANK0]`
- `[lpc176x_memorymap.h:LPC17_40_SRAM_BANK1]`
- `[lpc176x_memorymap.h:LPC17_40_GPIO_BASE]`
- `[lpc176x_memorymap.h:LPC17_40_APB_BASE]`
- `[lpc176x_memorymap.h:LPC17_40_APB0_BASE]`
- `[lpc176x_memorymap.h:LPC17_40_APB1_BASE]`
- `[lpc176x_memorymap.h:LPC17_40_AHB_BASE]`
- `[lpc176x_memorymap.h:LPC17_40_CORTEXM3_BASE]`
- `[lpc176x_pinconfig.h:GPIO_CAN1_RD_1]`
- `[lpc176x_pinconfig.h:GPIO_UART3_TXD_1]`
- `[lpc176x_pinconfig.h:GPIO_I2C1_SDA_1]`
- `[lpc176x_pinconfig.h:GPIO_CAN1_TD_1]`
- `[lpc176x_pinconfig.h:GPIO_UART3_RXD_1]`
- `[lpc176x_pinconfig.h:GPIO_I2C1_SCL_1]`
- `[lpc176x_pinconfig.h:GPIO_UART0_TXD]`
- `[lpc176x_pinconfig.h:GPIO_AD0p7]`
- `[lpc176x_pinconfig.h:GPIO_UART0_RXD]`
- `[lpc176x_pinconfig.h:GPIO_AD0p6]`
- `[lpc176x_pinconfig.h:GPIO_I2S_RXCLK_1]`
- `[lpc176x_pinconfig.h:GPIO_CAN2_RD_1]`
- `[lpc176x_pinconn.h:LPC17_40_PINCONN_PINSEL0_OFFSET]`
- `[lpc176x_pinconn.h:LPC17_40_PINCONN_PINSEL1_OFFSET]`
- `[lpc176x_pinconn.h:LPC17_40_PINCONN_PINSEL2_OFFSET]`
- `[lpc176x_pinconn.h:LPC17_40_PINCONN_PINSEL3_OFFSET]`
- `[lpc176x_pinconn.h:LPC17_40_PINCONN_PINSEL4_OFFSET]`
- `[lpc176x_pinconn.h:LPC17_40_PINCONN_PINSEL7_OFFSET]`

## Invariants
- `[lpc17_40_memorymap.h:#error]` Compile-time guard: Unrecognized LPC17xx/LPC40xx family
- `[lpc17_40_pinconfig.h:#error]` Compile-time guard: Unrecognized LPC17xx/LPC40xx family
- `[lpc17_40_pinconn.h:#error]` Compile-time guard: Unrecognized LPC17xx/LPC40xx family
- `[lpc17_40_syscon.h:#error]` Compile-time guard: Unrecognized LPC17xx/LPC40xx family

## Side Effects
- None

## Verification
- Run: `make test`
