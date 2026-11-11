# `tm4c1294-launchpad/src` Component (`boards/arm/tiva/tm4c1294-launchpad/src`)

## Overview
Board-level C implementation (`src`) for `tm4c1294-launchpad` (`arm/tiva`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 11 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[tm4c1294-launchpad.h:tm4c_ssidev_initialize]` Public declaration `tm4c_ssidev_initialize()`
- `[tm4c1294-launchpad.h:tm4c_led_initialize]` Public declaration `tm4c_led_initialize()`
- `[tm4c1294-launchpad.h:tm4c_bringup]` Public declaration `tm4c_bringup()`
- `[tm4c1294-launchpad.h:tiva_timer_configure]` Public declaration `tiva_timer_configure()`
- `[tm4c1294-launchpad.h:tm4c_can_setup]` Public declaration `tm4c_can_setup()`
- `[tm4c1294-launchpad.h:hciuart_dev_initialize]` Public declaration `hciuart_dev_initialize()`
- `[tm4c1294-launchpad.h:HAVE_HCIUART]` Hardware/board configuration macros (`HAVE_HCIUART`, `HCIUART_SERDEV`, `HAVE_I2CTOOL`, `TIVA_PROCFS_MOUNTPOINT`, `GPIO_LED_D1`, `GPIO_LED_D2` (+8 more))
- `[tm4c_autoleds.c:tm4c_led_initialize]` Public function `tm4c_led_initialize()`
- `[tm4c_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[tm4c_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[tm4c_boot.c:tiva_boardinitialize]` Public function `tiva_boardinitialize()`
- `[tm4c_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[tm4c_bringup.c:tm4c_bmp280_setup]` Public function `tm4c_bmp280_setup()`
- `[tm4c_bringup.c:tm4c_bringup]` Public function `tm4c_bringup()`
- `[tm4c_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[tm4c_buttons.c:board_buttons]` Public function `board_buttons()`
- `[tm4c_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[tm4c_can.c:tm4c_can_setup]` Public function `tm4c_can_setup()`
- `[tm4c_ethernet.c:tiva_ethernetmac]` Public function `tiva_ethernetmac()`
- `[tm4c_hciuart.c:hciuart_dev_initialize]` Public function `hciuart_dev_initialize()`
- `[tm4c_reset.c:board_reset]` Public function `board_reset()`
- `[tm4c_timer.c:tiva_timer_configure]` Public function `tiva_timer_configure()`
- `[tm4c_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- *(+2 additional symbols across 11 files)*

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_BLUETOOTH_UART`, `CONFIG_BOARDCTL_RESET`, `CONFIG_DK_TM4C129X_TIMER`, `CONFIG_TIVA_CAN` (+2 more)
- `[tm4c1294-launchpad.h:#error]` Compile-time guard: `No HCI UART specified`
- `[tm4c_bringup.c:tm4c_bmp280_setup]` Validates preconditions and returns `-ENODEV`, `-ENOMEM` on failure
- `[tm4c_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[tm4c_ethernet.c:DEBUGASSERT]` Requires `user0 != 0xffffffff && user1 != 0xffffffff`
- `[tm4c_timer.c:#error]` Compile-time guard: `CONFIG_TIMER is not defined`
- `[tm4c_timer.c:#error]` Compile-time guard: `CONFIG_TIVA_TIMER32_PERIODIC is not defined`

## Side Effects
- `[tm4c_autoleds.c:tm4c_led_initialize]` Configures or drives hardware GPIO pins
- `[tm4c_boot.c:tiva_boardinitialize]` Initializes/registers kernel devices or filesystems (`tm4c_led_initialize()`, `tm4c_ssidev_initialize()`)
- `[tm4c_bringup.c:tm4c_bmp280_setup]` Initializes/registers kernel devices or filesystems (`bmi160_register()`, `bmp280_register()`, `btn_lower_initialize()`, `hciuart_dev_initialize()`, `i2c_register()`)
- `[tm4c_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[tm4c_can.c:tm4c_can_setup]` Configures or drives hardware GPIO pins
- `[tm4c_can.c:tm4c_can_setup]` Initializes/registers kernel devices or filesystems (`tiva_can_initialize()`)
- `[tm4c_hciuart.c:hciuart_dev_initialize]` Initializes/registers kernel devices or filesystems (`btuart_register()`, `hciuart_initialize()`)
- `[tm4c_timer.c:tiva_timer_configure]` Initializes/registers kernel devices or filesystems (`tiva_timer_register()`)
- `[tm4c_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh tm4c1294-launchpad:nsh && make`
