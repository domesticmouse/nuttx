# `olimex-stm32-h405/src` Component (`boards/arm/stm32f4/olimex-stm32-h405/src`)

## Overview
Board-level C implementation (`src`) for `olimex-stm32-h405` (`arm/stm32f4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[olimex-stm32-h405.h:stm32_usbinitialize]` Public declaration `stm32_usbinitialize()`
- `[olimex-stm32-h405.h:stm32_adc_setup]` Public declaration `stm32_adc_setup()`
- `[olimex-stm32-h405.h:stm32_can_setup]` Public declaration `stm32_can_setup()`
- `[olimex-stm32-h405.h:GPIO_LED_STATUS]` Hardware/board configuration macros (`GPIO_LED_STATUS`, `MIN_IRQBUTTON`, `MAX_IRQBUTTON`, `NUM_IRQBUTTONS`, `GPIO_BTN_BUT`, `GPIO_OTGFS_VBUS`)
- `[stm32_adc.c:stm32_adc_setup]` Public function `stm32_adc_setup()`
- `[stm32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[stm32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[stm32_buttons.c:board_buttons]` Public function `board_buttons()`
- `[stm32_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[stm32_can.c:stm32_can_setup]` Public function `stm32_can_setup()`
- `[stm32_usb.c:stm32_usbinitialize]` Public function `stm32_usbinitialize()`
- `[stm32_usb.c:stm32_usbsuspend]` Public function `stm32_usbsuspend()`
- `[stm32_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[stm32_userleds.c:board_userled]` Public function `board_userled()`
- `[stm32_userleds.c:board_userled_all]` Public function `board_userled_all()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ADC`, `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_STM32_CAN_CHARDRIVER`, `CONFIG_STM32_OTGFS`
- `[stm32_adc.c:stm32_adc_setup]` Validates preconditions and returns `-ENODEV`, `-ENOSYS` on failure
- `[stm32_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[stm32_can.c:stm32_can_setup]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[stm32_adc.c:stm32_adc_setup]` Configures or drives hardware GPIO pins
- `[stm32_adc.c:stm32_adc_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`)
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `board_button_initialize()`)
- `[stm32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[stm32_can.c:stm32_can_setup]` Initializes/registers kernel devices or filesystems (`can_register()`)
- `[stm32_usb.c:stm32_usbinitialize]` Configures or drives hardware GPIO pins
- `[stm32_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh olimex-stm32-h405:usbnsh && make`
