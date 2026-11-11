# `stm32l476-mdk/src` Component (`boards/arm/stm32l4/stm32l476-mdk/src`)

## Overview
Board-level C implementation (`src`) for `stm32l476-mdk` (`arm/stm32l4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 7 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[stm32l476-mdk.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[stm32l476-mdk.h:stm32_spiinitialize]` Public declaration `stm32_spiinitialize()`
- `[stm32l476-mdk.h:HAVE_PROC]` Hardware/board configuration macros (`HAVE_PROC`, `HAVE_RTC_DRIVER`, `HAVE_USERLED_DRIVER`, `GPIO_LED_RED`, `GPIO_LED_GREEN`, `GPIO_LED_WHITE` (+8 more))
- `[stm32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[stm32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_boot.c:stm32_board_initialize]` Public function `stm32_board_initialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_boot.c:board_uniqueid]` Public function `board_uniqueid()`
- `[stm32_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[stm32_buttons.c:board_buttons]` Public function `board_buttons()`
- `[stm32_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[stm32_clockconfig.c:stm32_board_clockconfig]` Public function `stm32_board_clockconfig()`
- `[stm32_spi.c:stm32_spiinitialize]` Public function `stm32_spiinitialize()`
- `[stm32_spi.c:stm32_spi1select]` Public function `stm32_spi1select()`
- `[stm32_spi.c:stm32_spi1status]` Public function `stm32_spi1status()`
- `[stm32_spi.c:stm32_spi2select]` Public function `stm32_spi2select()`
- `[stm32_spi.c:stm32_spi2status]` Public function `stm32_spi2status()`
- `[stm32_spi.c:stm32_spi3select]` Public function `stm32_spi3select()`
- `[stm32_spi.c:stm32_spi3status]` Public function `stm32_spi3status()`
- `[stm32_spi.c:stm32_spi1cmddata]` Public function `stm32_spi1cmddata()`
- `[stm32_spi.c:stm32_spi2cmddata]` Public function `stm32_spi2cmddata()`
- `[stm32_spi.c:stm32_spi3cmddata]` Public function `stm32_spi3cmddata()`
- *(+3 additional symbols across 7 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BOARD_STM32_CUSTOM_CLOCKCONFIG`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`
- `[stm32_boot.c:stm32_board_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[stm32_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure

## Side Effects
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_boot.c:stm32_board_initialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `nx_mount()`, `rtc_initialize()`, `userled_lower_initialize()`)
- `[stm32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[stm32_clockconfig.c:stm32_board_clockconfig]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[stm32_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh stm32l476-mdk:nsh && make`
