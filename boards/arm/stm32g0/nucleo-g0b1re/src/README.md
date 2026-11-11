# `nucleo-g0b1re/src` Component (`boards/arm/stm32g0/nucleo-g0b1re/src`)

## Overview
Board-level C implementation (`src`) for `nucleo-g0b1re` (`arm/stm32g0`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 6 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[nucleo-g0b1re.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[nucleo-g0b1re.h:stm32_adc_setup]` Public declaration `stm32_adc_setup()`
- `[nucleo-g0b1re.h:GPIO_LED1]` Hardware/board configuration macros (`GPIO_LED1`, `LED_DRIVER_PATH`, `MIN_IRQBUTTON`, `MAX_IRQBUTTON`, `NUM_IRQBUTTONS`, `GPIO_BTN_USER`)
- `[stm32_adc.c:stm32_adc_setup]` Public function `stm32_adc_setup()`
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

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ADC`, `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`
- `[stm32_adc.c:stm32_adc_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure

## Side Effects
- `[stm32_adc.c:stm32_adc_setup]` Configures or drives hardware GPIO pins
- `[stm32_adc.c:stm32_adc_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`)
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_boot.c:stm32_boardinitialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `stm32_spidev_initialize()`)
- `[stm32_boot.c:stm32_boardinitialize]` Modifies interrupt controller or critical-section state
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`cdcacm_initialize()`, `stm32_common_initialize()`, `userled_lower_initialize()`)
- `[stm32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh nucleo-g0b1re:nsh && make`
