# `stm32l0538-disco/src` Component (`boards/arm/stm32l0/stm32l0538-disco/src`)

## Overview
Board-level C implementation (`src`) for `stm32l0538-disco` (`arm/stm32l0`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[stm32l0538-disco.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[stm32l0538-disco.h:GPIO_LED1]` Hardware/board configuration macros (`GPIO_LED1`, `GPIO_LED2`, `LED_DRIVER_PATH`, `MIN_IRQBUTTON`, `MAX_IRQBUTTON`, `NUM_IRQBUTTONS` (+1 more))
- `[stm32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[stm32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_bringup.c:stm32_bringup]` Public function `stm32_bringup()`
- `[stm32_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[stm32_buttons.c:board_buttons]` Public function `board_buttons()`
- `[stm32_buttons.c:board_button_irq]` Public function `board_button_irq()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`
- `[stm32_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure

## Side Effects
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`btn_lower_initialize()`, `userled_lower_initialize()`)
- `[stm32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh stm32l0538-disco:nsh && make`
