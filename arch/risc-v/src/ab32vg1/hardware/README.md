# hardware (`nuttx/arch/risc-v/src/ab32vg1/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/risc-v/src/ab32vg1/hardware`, providing 6 header file(s) and 0 source file(s) (including `ab32vg1_clk.h`, `ab32vg1_gpio.h`, `ab32vg1_memorymap.h`, `ab32vg1_pic.h`).

## Interface
- `[ab32vg1_clk.h:AB32VG1_CLKCON0]`
- `[ab32vg1_clk.h:AB32VG1_WDTCON]`
- `[ab32vg1_clk.h:AB32VG1_CLKCON1]`
- `[ab32vg1_clk.h:AB32VG1_SPI0BAUD]`
- `[ab32vg1_clk.h:AB32VG1_PLL0DIV]`
- `[ab32vg1_clk.h:AB32VG1_PLL0CON]`
- `[ab32vg1_clk.h:AB32VG1_CLKCON2]`
- `[ab32vg1_clk.h:AB32VG1_CLKGAT0]`
- `[ab32vg1_clk.h:AB32VG1_CLKCON3]`
- `[ab32vg1_clk.h:AB32VG1_CLKGAT1]`
- `[ab32vg1_clk.h:CLKCON0_SYSCLK_RC2M]`
- `[ab32vg1_clk.h:CLKCON0_SYSCLK_SPLL]`
- `[ab32vg1_gpio.h:AB32VG1_GPIOA_BASE]`
- `[ab32vg1_gpio.h:AB32VG1_GPIOB_BASE]`
- `[ab32vg1_gpio.h:AB32VG1_GPIOE_BASE]`
- `[ab32vg1_gpio.h:AB32VG1_GPIOF_BASE]`
- `[ab32vg1_gpio.h:AB32VG1_GPIO_SET_OFFSET]`
- `[ab32vg1_gpio.h:AB32VG1_GPIO_CLR_OFFSET]`
- `[ab32vg1_gpio.h:AB32VG1_GPIO_DATA_OFFSET]`
- `[ab32vg1_gpio.h:AB32VG1_GPIO_DIR_OFFSET]`
- `[ab32vg1_gpio.h:AB32VG1_GPIO_DE_OFFSET]`
- `[ab32vg1_gpio.h:AB32VG1_GPIO_FEN_OFFSET]`
- `[ab32vg1_gpio.h:AB32VG1_GPIO_DRV_OFFSET]`
- `[ab32vg1_gpio.h:AB32VG1_GPIO_PU_OFFSET]`
- `[ab32vg1_memorymap.h:AB32VG1_SFR0_BASE]`
- `[ab32vg1_memorymap.h:AB32VG1_SFR1_BASE]`
- `[ab32vg1_memorymap.h:AB32VG1_SFR2_BASE]`
- `[ab32vg1_memorymap.h:AB32VG1_SFR3_BASE]`
- `[ab32vg1_memorymap.h:AB32VG1_SFR4_BASE]`
- `[ab32vg1_memorymap.h:AB32VG1_SFR5_BASE]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
