# `efm32-g8xx-stk/src` Component (`boards/arm/efm32/efm32-g8xx-stk/src`)

## Overview
Board-level C implementation (`src`) for `efm32-g8xx-stk` (`arm/efm32`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 4 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[efm32-g8xx-stk.h:GPIO_BC_EN]` Hardware/board configuration macros (`GPIO_BC_EN`, `GPIO_LED0`, `GPIO_LED1`, `GPIO_LED2`, `GPIO_LED3`)
- `[efm32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[efm32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[efm32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[efm32_boot.c:efm32_boardinitialize]` Public function `efm32_boardinitialize()`
- `[efm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[efm32_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[efm32_userleds.c:board_userled]` Public function `board_userled()`
- `[efm32_userleds.c:board_userled_all]` Public function `board_userled_all()`
- `[efm32_userleds.c:efm32_led_pminitialize]` Public function `efm32_led_pminitialize()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_LEDS`

## Side Effects
- `[efm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[efm32_boot.c:efm32_boardinitialize]` Configures or drives hardware GPIO pins
- `[efm32_boot.c:efm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[efm32_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins
- `[efm32_userleds.c:board_userled_initialize]` Initializes/registers kernel devices or filesystems (`pm_register()`)

## Verification
- Run: `./tools/configure.sh efm32-g8xx-stk:nsh && make`
