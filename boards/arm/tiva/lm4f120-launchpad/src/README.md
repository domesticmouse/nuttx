# `lm4f120-launchpad/src` Component (`boards/arm/tiva/lm4f120-launchpad/src`)

## Overview
Board-level C implementation (`src`) for `lm4f120-launchpad` (`arm/tiva`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 4 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[lmf4120-launchpad.h:lm4f_spidev_initialize]` Public declaration `lm4f_spidev_initialize()`
- `[lmf4120-launchpad.h:lm4f_led_initialize]` Public declaration `lm4f_led_initialize()`
- `[lmf4120-launchpad.h:GPIO_LED_R]` Hardware/board configuration macros (`GPIO_LED_R`, `GPIO_LED_G`, `GPIO_LED_B`, `GPIO_SW1`, `GPIO_SW2`)
- `[lm4f_autoleds.c:lm4f_led_initialize]` Public function `lm4f_led_initialize()`
- `[lm4f_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[lm4f_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[lm4f_boot.c:tiva_boardinitialize]` Public function `tiva_boardinitialize()`
- `[lm4f_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[lm4f_ssi.c:lm4f_spidev_initialize]` Public function `lm4f_spidev_initialize()`
- `[lm4f_ssi.c:tiva_ssiselect]` Public function `tiva_ssiselect()`
- `[lm4f_ssi.c:tiva_ssistatus]` Public function `tiva_ssistatus()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_LEDS`

## Side Effects
- `[lm4f_autoleds.c:lm4f_led_initialize]` Configures or drives hardware GPIO pins
- `[lm4f_boot.c:tiva_boardinitialize]` Initializes/registers kernel devices or filesystems (`lm4f_led_initialize()`, `lm4f_spidev_initialize()`)

## Verification
- Run: `./tools/configure.sh lm4f120-launchpad:nsh && make`
