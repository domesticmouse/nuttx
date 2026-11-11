# `xx3803/src` Component (`boards/sparc/bm3803/xx3803/src`)

## Overview
Board-level C implementation (`src`) for `xx3803` (`sparc/bm3803`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[xx3803.h:bm3803_led_initialize]` Public declaration `bm3803_led_initialize()`
- `[xx3803.h:bm3803_am29lv_initialize]` Public declaration `bm3803_am29lv_initialize()`
- `[xx3803.h:bm3803_1553b_initialize]` Public declaration `bm3803_1553b_initialize()`
- `[xx3803.h:bm3803_spacewire_initialize]` Public declaration `bm3803_spacewire_initialize()`
- `[xx3803.h:xx3803_watchdog_initialize]` Public declaration `xx3803_watchdog_initialize()`
- `[xx3803.h:bm3803_fpga_uart_initialize]` Public declaration `bm3803_fpga_uart_initialize()`
- `[xx3803.h:bm3803_secpulse_initialize]` Public declaration `bm3803_secpulse_initialize()`
- `[xx3803.h:GPIO_PULSE_IRQ]` Hardware/board configuration macros (`GPIO_PULSE_IRQ`, `GPIO_1553B_IRQ`, `GPIO_RS422_IRQ`, `GPIO_SPACEWIRE_IRQ`, `BM3803_PROCFS_MOUNTPOINT`)
- `[bm3803_am29lv.c:bm3803_am29lv_initialize]` Public function `bm3803_am29lv_initialize()`
- `[bm3803_boot.c:bm3803_boardinitialize]` Public function `bm3803_boardinitialize()`
- `[bm3803_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[bm3803_reset.c:board_reset]` Public function `board_reset()`
- `[bm3803_wdt.c:xx3803_watchdog_initialize]` Public function `xx3803_watchdog_initialize()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_BOARDCTL_RESET`, `CONFIG_MTD_AM29LV`, `CONFIG_XX3803_WDG`
- `[bm3803_am29lv.c:bm3803_am29lv_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[bm3803_wdt.c:DEBUGASSERT]` Requires `taskid > 0`
- `[bm3803_wdt.c:#error]` Compile-time guard: `No watchdog configured`

## Side Effects
- `[bm3803_am29lv.c:bm3803_am29lv_initialize]` Initializes/registers kernel devices or filesystems (`am29lv_initialize()`, `mtdpara_register()`, `rammtd_initialize()`)
- `[bm3803_boot.c:bm3803_boardinitialize]` Initializes/registers kernel devices or filesystems (`bm3803_am29lv_initialize()`, `oneshot_initialize()`, `oneshot_register()`, `xx3803_watchdog_initialize()`)

## Verification
- Run: `./tools/configure.sh xx3803:nsh && make`
