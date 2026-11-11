# `s698pm-dkit/src` Component (`boards/sparc/s698pm/s698pm-dkit/src`)

## Overview
Board-level C implementation (`src`) for `s698pm-dkit` (`sparc/s698pm`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 3 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[s698pm-dkit.h:s698pm_led_initialize]` Public declaration `s698pm_led_initialize()`
- `[s698pm-dkit.h:s698pm_dkit_watchdog_initialize]` Public declaration `s698pm_dkit_watchdog_initialize()`
- `[s698pm-dkit.h:S698PM_PROCFS_MOUNTPOINT]` Hardware/board configuration macros (`S698PM_PROCFS_MOUNTPOINT`)
- `[s698pm_boot.c:s698pm_boardinitialize]` Public function `s698pm_boardinitialize()`
- `[s698pm_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[s698pm_wdt.c:s698pm_dkit_watchdog_initialize]` Public function `s698pm_dkit_watchdog_initialize()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_S698PM_WDG`
- `[s698pm_wdt.c:DEBUGASSERT]` Requires `taskid > 0`
- `[s698pm_wdt.c:#error]` Compile-time guard: `No watchdog configured`

## Side Effects
- `[s698pm_boot.c:s698pm_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `s698pm_dkit_watchdog_initialize()`)

## Verification
- Run: `./tools/configure.sh s698pm-dkit:nsh && make`
