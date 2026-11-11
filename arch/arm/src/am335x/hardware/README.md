# hardware (`nuttx/arch/arm/src/am335x/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/am335x/hardware`, providing 15 header file(s) and 0 source file(s) (including `am3358_memorymap.h`, `am3358_pinmux.h`, `am335x_dcan.h`, `am335x_gpio.h`).

## Interface
- `[am3358_memorymap.h:__CONCAT]`
- `[am3358_memorymap.h:MKULONG]`
- `[am3358_memorymap.h:AM335X_GPMC_PSECTION]`
- `[am3358_memorymap.h:AM335X_BROM_PSECTION]`
- `[am3358_memorymap.h:AM335X_ISRAM_PSECTION]`
- `[am3358_memorymap.h:AM335X_OCMC0_PSECTION]`
- `[am3358_memorymap.h:AM335X_PERIPH_PSECTION]`
- `[am3358_memorymap.h:AM335X_DDR_PSECTION]`
- `[am3358_memorymap.h:AM335X_BROM_OFFSET]`
- `[am3358_memorymap.h:AM335X_ISRAM_OFFSET]`
- `[am3358_memorymap.h:AM335X_OCMC0_OFFSET]`
- `[am3358_memorymap.h:AM335X_L3_FAST_CFG_OFFSET]`
- `[am3358_pinmux.h:GPIO_EMU0]`
- `[am3358_pinmux.h:GPIO_EMU1]`
- `[am3358_pinmux.h:GPIO_EMU2_1]`
- `[am3358_pinmux.h:GPIO_EMU2_2]`
- `[am3358_pinmux.h:GPIO_EMU2_3]`
- `[am3358_pinmux.h:GPIO_EMU3_1]`
- `[am3358_pinmux.h:GPIO_EMU3_2]`
- `[am3358_pinmux.h:GPIO_EMU3_3]`
- `[am3358_pinmux.h:GPIO_EMU4_1]`
- `[am3358_pinmux.h:GPIO_EMU4_2]`
- `[am3358_pinmux.h:GPIO_EMU4_3]`
- `[am3358_pinmux.h:GPIO_LCD_PCLK]`
- `[am335x_dcan.h:AM335X_DCAN_CTL_OFFSET]`
- `[am335x_dcan.h:AM335X_DCAN_ES_OFFSET]`
- `[am335x_dcan.h:AM335X_DCAN_ERRC_OFFSET]`
- `[am335x_dcan.h:AM335X_DCAN_BTR_OFFSET]`
- `[am335x_dcan.h:AM335X_DCAN_INT_OFFSET]`
- `[am335x_dcan.h:AM335X_DCAN_TEST_OFFSET]`

## Invariants
- `[am3358_memorymap.h:#error]` Compile-time guard: Only one of PGTABLE_BASE_PADDR or PGTABLE_BASE_VADDR is defined
- `[am335x_memorymap.h:#error]` Compile-time guard: Unrecognized AM335X architecture
- `[am335x_pinmux.h:#error]` Compile-time guard: Unrecognized AM335X architecture

## Side Effects
- None

## Verification
- Run: `make test`
