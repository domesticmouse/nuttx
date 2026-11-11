# hardware (`nuttx/arch/arm/src/max326xx/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/max326xx/hardware`, providing 30 header file(s) and 0 source file(s) (including `max32620_30_memorymap.h`, `max32660_flc.h`, `max32660_gcr.h`, `max32660_gpio.h`).

## Interface
- `[max32620_30_memorymap.h:MAX326_CODE_BASE]`
- `[max32620_30_memorymap.h:MAX326_SPIXIP_BASE]`
- `[max32620_30_memorymap.h:MAX326_SRAM_BASE]`
- `[max32620_30_memorymap.h:MAX326_PERIPH_BASE]`
- `[max32620_30_memorymap.h:MAX326_APB_BASE]`
- `[max32620_30_memorymap.h:MAX326_AHB_BASE]`
- `[max32620_30_memorymap.h:MAX326_SYSTEM_BASE]`
- `[max32620_30_memorymap.h:MAX326_SCS_BASE]`
- `[max32620_30_memorymap.h:MAX326_SYSMAN_BASE]`
- `[max32620_30_memorymap.h:MAX326_CLKMAN_BASE]`
- `[max32620_30_memorymap.h:MAX326_PWRMAN_BASE]`
- `[max32620_30_memorymap.h:MAX326_RTC_BASE]`
- `[max32660_flc.h:MAX326_FLC_ADDR_OFFSET]`
- `[max32660_flc.h:MAX326_FLC_CLKDIV_OFFSET]`
- `[max32660_flc.h:MAX326_FLC_CTRL_OFFSET]`
- `[max32660_flc.h:MAX326_FLC_INTR_OFFSET]`
- `[max32660_flc.h:MAX326_FLC_DATA0_OFFSET]`
- `[max32660_flc.h:MAX326_FLC_DATA1_OFFSET]`
- `[max32660_flc.h:MAX326_FLC_DATA2_OFFSET]`
- `[max32660_flc.h:MAX326_FLC_DATA3_OFFSET]`
- `[max32660_flc.h:MAX326_FLC_ADDR]`
- `[max32660_flc.h:MAX326_FLC_CLKDIV]`
- `[max32660_flc.h:MAX326_FLC_CTRL]`
- `[max32660_flc.h:MAX326_FLC_INTR]`
- `[max32660_gcr.h:MAX326_GCR_SCON_OFFSET]`
- `[max32660_gcr.h:MAX326_GCR_RST0_OFFSET]`
- `[max32660_gcr.h:MAX326_GCR_CLKCTRL_OFFSET]`
- `[max32660_gcr.h:MAX326_GCR_PM_OFFSET]`
- `[max32660_gcr.h:MAX326_GCR_PCLKDIS0_OFFSET]`
- `[max32660_gcr.h:MAX326_GCR_MEMCTRL_OFFSET]`

## Invariants
- `[max326_flc.h:#error]` Compile-time guard: Unsupported MAX326XX family
- `[max326_gcr.h:#error]` Compile-time guard: Unsupported MAX326XX family
- `[max326_gpio.h:#error]` Compile-time guard: Unsupported MAX326XX family
- `[max326_memorymap.h:#error]` Compile-time guard: Unsupported MAX326XX family
- `[max326_pinmux.h:#error]` Compile-time guard: Unsupported MAX326XX family
- `[max326_rtc.h:#error]` Compile-time guard: Unsupported MAX326XX family
- `[max326_spi.h:#error]` Compile-time guard: Unsupported MAX326XX family
- `[max326_tmr.h:#error]` Compile-time guard: Unsupported MAX326XX family
- `[max326_uart.h:#error]` Compile-time guard: Unsupported MAX326XX family
- `[max326_wdt.h:#error]` Compile-time guard: Unsupported MAX326XX family

## Side Effects
- None

## Verification
- Run: `make test`
