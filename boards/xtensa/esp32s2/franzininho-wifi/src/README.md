# `franzininho-wifi/src` Component (`boards/xtensa/esp32s2/franzininho-wifi/src`)

## Overview
Board-level C implementation (`src`) for `franzininho-wifi` (`xtensa/esp32s2`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[franzininho-wifi.h:esp32s2_bringup]` Public declaration `esp32s2_bringup()`
- `[franzininho-wifi.h:board_oneshot_init]` Public declaration `board_oneshot_init()`
- `[franzininho-wifi.h:BUTTON_BOOT]` Hardware/board configuration macros (`BUTTON_BOOT`, `TIMER0`, `TIMER1`, `TIMER2`, `TIMER3`, `ONESHOT_TIMER` (+1 more))
- `[esp32s2_boot.c:esp32s2_board_initialize]` Public function `esp32s2_board_initialize()`
- `[esp32s2_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[esp32s2_bringup.c:esp32s2_bringup]` Public function `esp32s2_bringup()`
- `[esp32s2_oneshot.c:board_oneshot_init]` Public function `board_oneshot_init()`
- `[esp32s2_reset.c:board_reset]` Public function `board_reset()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_BOARDCTL_RESET`, `CONFIG_ONESHOT`
- `[esp32s2_oneshot.c:board_oneshot_init]` Validates preconditions and returns `-EBUSY` on failure

## Side Effects
- `[esp32s2_bringup.c:esp32s2_bringup]` Initializes/registers kernel devices or filesystems (`esp32s2_timer_initialize()`, `nx_mount()`)
- `[esp32s2_oneshot.c:board_oneshot_init]` Initializes/registers kernel devices or filesystems (`oneshot_initialize()`, `oneshot_register()`)

## Verification
- Run: `./tools/configure.sh franzininho-wifi:nsh && make`
