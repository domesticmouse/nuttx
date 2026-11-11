# `tm4c129e-launchpad/src` Component (`boards/arm/tiva/tm4c129e-launchpad/src`)

## Overview
Board-level C implementation (`src`) for `tm4c129e-launchpad` (`arm/tiva`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 9 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[tm4c129e-launchpad.h:tm4c_ssidev_initialize]` Public declaration `tm4c_ssidev_initialize()`
- `[tm4c129e-launchpad.h:tm4c_led_initialize]` Public declaration `tm4c_led_initialize()`
- `[tm4c129e-launchpad.h:tm4c_bringup]` Public declaration `tm4c_bringup()`
- `[tm4c129e-launchpad.h:tiva_timer_configure]` Public declaration `tiva_timer_configure()`
- `[tm4c129e-launchpad.h:hciuart_dev_initialize]` Public declaration `hciuart_dev_initialize()`
- `[tm4c129e-launchpad.h:HAVE_HCIUART]` Hardware/board configuration macros (`HAVE_HCIUART`, `HCIUART_SERDEV`, `HAVE_I2CTOOL`, `GPIO_LED_D1`, `GPIO_LED_D2`, `GPIO_LED_D3` (+7 more))
- `[tm4c_autoleds.c:tm4c_led_initialize]` Public function `tm4c_led_initialize()`
- `[tm4c_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[tm4c_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[tm4c_boot.c:tiva_boardinitialize]` Public function `tiva_boardinitialize()`
- `[tm4c_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[tm4c_bringup.c:tm4c_bringup]` Public function `tm4c_bringup()`
- `[tm4c_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[tm4c_buttons.c:board_buttons]` Public function `board_buttons()`
- `[tm4c_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[tm4c_ethernet.c:tiva_ethernetmac]` Public function `tiva_ethernetmac()`
- `[tm4c_hciuart.c:hciuart_dev_initialize]` Public function `hciuart_dev_initialize()`
- `[tm4c_timer.c:tiva_timer_configure]` Public function `tiva_timer_configure()`
- `[tm4c_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[tm4c_userleds.c:board_userled]` Public function `board_userled()`
- `[tm4c_userleds.c:board_userled_all]` Public function `board_userled_all()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_BLUETOOTH_UART`, `CONFIG_DK_TM4C129X_TIMER`, `CONFIG_TIVA_ETHERNET`, `CONFIG_TIVA_HCIUART`
- `[tm4c129e-launchpad.h:#error]` Compile-time guard: `No HCI UART specified`
- `[tm4c_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[tm4c_ethernet.c:DEBUGASSERT]` Requires `user0 != 0xffffffff && user1 != 0xffffffff`
- `[tm4c_timer.c:#error]` Compile-time guard: `CONFIG_TIMER is not defined`
- `[tm4c_timer.c:#error]` Compile-time guard: `CONFIG_TIVA_TIMER32_PERIODIC is not defined`

## Side Effects
- `[tm4c_autoleds.c:tm4c_led_initialize]` Configures or drives hardware GPIO pins
- `[tm4c_boot.c:tiva_boardinitialize]` Initializes/registers kernel devices or filesystems (`tm4c_led_initialize()`, `tm4c_ssidev_initialize()`)
- `[tm4c_bringup.c:tm4c_bringup]` Initializes/registers kernel devices or filesystems (`btn_lower_initialize()`, `hciuart_dev_initialize()`, `i2c_register()`, `pwm_register()`, `qe_register()`)
- `[tm4c_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[tm4c_hciuart.c:hciuart_dev_initialize]` Initializes/registers kernel devices or filesystems (`btuart_register()`, `hciuart_initialize()`)
- `[tm4c_timer.c:tiva_timer_configure]` Initializes/registers kernel devices or filesystems (`tiva_timer_register()`)
- `[tm4c_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh tm4c129e-launchpad:nsh && make`
