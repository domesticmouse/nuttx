# hardware (`nuttx/arch/risc-v/src/allwinner-d1/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/risc-v/src/allwinner-d1/hardware`, providing 4 header file(s) and 0 source file(s) (including `allwinner_d1_memorymap.h`, `allwinner_d1_plic.h`, `allwinner_d1_timer.h`, `allwinner_d1_wdt.h`).

## Interface
- `[allwinner_d1_memorymap.h:ALLWINNER_D1_PIO_BASE]`
- `[allwinner_d1_memorymap.h:ALLWINNER_D1_CCU_BASE]`
- `[allwinner_d1_memorymap.h:ALLWINNER_D1_TIMER_BASE]`
- `[allwinner_d1_memorymap.h:ALLWINNER_D1_UART0_BASE]`
- `[allwinner_d1_memorymap.h:ALLWINNER_D1_RISCV_WDT_BASE]`
- `[allwinner_d1_memorymap.h:ALLWINNER_D1_PLIC_BASE]`
- `[allwinner_d1_memorymap.h:ALLWINNER_D1_DRAM_BASE]`
- `[allwinner_d1_memorymap.h:ALLWINNER_D1_PB_CFG1]`
- `[allwinner_d1_memorymap.h:ALLWINNER_D1_UART_BGR]`
- `[allwinner_d1_plic.h:ALLWINNER_D1_PLIC_NDEV]`
- `[allwinner_d1_plic.h:ALLWINNER_D1_PLIC_PRIORITY]`
- `[allwinner_d1_plic.h:ALLWINNER_D1_PLIC_ENABLE]`
- `[allwinner_d1_plic.h:ALLWINNER_D1_PLIC_THRESHOLD]`
- `[allwinner_d1_plic.h:ALLWINNER_D1_PLIC_CLAIM]`
- `[allwinner_d1_timer.h:ALLWINNER_D1_TIMER_IRQ_EN]`
- `[allwinner_d1_timer.h:ALLWINNER_D1_TIMER_IRQ_STATUS]`
- `[allwinner_d1_timer.h:ALLWINNER_D1_TIMER_CTRL]`
- `[allwinner_d1_timer.h:ALLWINNER_D1_TIMER_INTERVAL]`
- `[allwinner_d1_timer.h:ALLWINNER_D1_TIMER_CURRENT]`
- `[allwinner_d1_timer.h:ALLWINNER_D1_TIMER_IRQ]`
- `[allwinner_d1_timer.h:ALLWINNER_D1_TIMER_CTRL_ENABLE]`
- `[allwinner_d1_timer.h:ALLWINNER_D1_TIMER_CTRL_RELOAD]`
- `[allwinner_d1_timer.h:ALLWINNER_D1_TIMER_CTRL_CLK_SRC_MASK]`
- `[allwinner_d1_timer.h:ALLWINNER_D1_TIMER_CTRL_CLK_OSC24M]`
- `[allwinner_d1_timer.h:ALLWINNER_D1_TIMER_CTRL_PRES_MASK]`
- `[allwinner_d1_timer.h:ALLWINNER_D1_TIMER_CTRL_PRES_DIV1]`
- `[allwinner_d1_wdt.h:ALLWINNER_D1_RISCV_WDT_MODE]`
- `[allwinner_d1_wdt.h:ALLWINNER_D1_RISCV_WDT_DISABLE_KEY]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
