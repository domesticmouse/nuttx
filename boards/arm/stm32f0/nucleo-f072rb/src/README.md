# `nucleo-f072rb/src` Component (`boards/arm/stm32f0/nucleo-f072rb/src`)

## Overview
Board-level C implementation (`src`) for `nucleo-f072rb` (`arm/stm32f0`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 6 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[nucleo-f072rb.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[nucleo-f072rb.h:GPIO_LD2]` Hardware/board configuration macros (`GPIO_LD2`, `MIN_IRQBUTTON`, `MAX_IRQBUTTON`, `NUM_IRQBUTTONS`, `GPIO_BTN_USER`)
- `[stm32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[stm32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:stm32_usb_setpullup]` Public function `stm32_usb_setpullup()`
- `[stm32_boot.c:stm32_usb_pullup_enabled]` Public function `stm32_usb_pullup_enabled()`
- `[stm32_boot.c:stm32_usbpullup]` Public function `stm32_usbpullup()`
- `[stm32_boot.c:stm32_usbsuspend]` Public function `stm32_usbsuspend()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_bringup.c:stm32_bringup]` Public function `stm32_bringup()`
- `[stm32_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[stm32_buttons.c:board_buttons]` Public function `board_buttons()`
- `[stm32_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[stm32_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[stm32_userleds.c:board_userled]` Public function `board_userled()`
- `[stm32_userleds.c:board_userled_all]` Public function `board_userled_all()`
- `[stm32_userleds.c:stm32_led_pminitialize]` Public function `stm32_led_pminitialize()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`
- `[stm32_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[stm32_userleds.c:DEBUGASSERT]` Requires `ret == OK`

## Side Effects
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_boot.c:stm32_boardinitialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[stm32_boot.c:stm32_boardinitialize]` Modifies interrupt controller or critical-section state
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`cdcacm_initialize()`, `stm32_common_initialize()`)
- `[stm32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[stm32_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_userleds.c:board_userled_initialize]` Initializes/registers kernel devices or filesystems (`pm_register()`)

## Verification
- Run: `./tools/configure.sh nucleo-f072rb:nsh && make`
