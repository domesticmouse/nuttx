# `avr32dev1/src` Component (`boards/avr/at32uc3/avr32dev1/src`)

## Overview
Board-level C implementation (`src`) for `avr32dev1` (`avr/at32uc3`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[avr32dev1.h:CONFIG_AVR32DEV_BUTTON1_IRQ]` Hardware/board configuration macros (`CONFIG_AVR32DEV_BUTTON1_IRQ`, `CONFIG_AVR32DEV_BUTTON2_IRQ`, `PINMUX_GPIO_LED1`, `PINMUX_GPIO_LED2`, `PINMUX_GPIO_BUTTON1`, `GPIO_BUTTON1_IRQ` (+2 more))
- `[avr32_boot.c:at32uc3_boardinitialize]` Public function `at32uc3_boardinitialize()`
- `[avr32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[avr32_bringup.c:avr32_bringup]` Public function `avr32_bringup()`
- `[avr32_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[avr32_buttons.c:board_buttons]` Public function `board_buttons()`
- `[avr32_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[avr32_leds.c:board_autoled_initializeialize]` Public function `board_autoled_initializeialize()`
- `[avr32_leds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[avr32_leds.c:board_autoled_off]` Public function `board_autoled_off()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`
- `[avr32_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure

## Side Effects
- `[avr32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[avr32_leds.c:board_autoled_initializeialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh avr32dev1:nsh && make`
