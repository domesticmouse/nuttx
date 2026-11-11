# `stm32vldiscovery/src` Component (`boards/arm/stm32f1/stm32vldiscovery/src`)

## Overview
Board-level C implementation (`src`) for `stm32vldiscovery` (`arm/stm32f1`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[stm32vldiscovery.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[stm32vldiscovery.h:stm32_led_initialize]` Public declaration `stm32_led_initialize()`
- `[stm32vldiscovery.h:GPIO_LED1]` Hardware/board configuration macros (`GPIO_LED1`, `MIN_IRQBUTTON`, `MAX_IRQBUTTON`, `NUM_IRQBUTTONS`, `GPIO_BTN_0`)
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_bringup.c:stm32_bringup]` Public function `stm32_bringup()`
- `[stm32_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[stm32_buttons.c:board_buttons]` Public function `board_buttons()`
- `[stm32_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[stm32_leds.c:stm32_led_initialize]` Public function `stm32_led_initialize()`
- `[stm32_leds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_leds.c:board_autoled_off]` Public function `board_autoled_off()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`
- `[stm32_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure

## Side Effects
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`stm32_led_initialize()`)
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`btn_lower_initialize()`, `nx_mount()`, `userled_lower_initialize()`)
- `[stm32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[stm32_leds.c:stm32_led_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh stm32vldiscovery:nsh && make`
