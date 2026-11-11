# `at32f437-mini/src` Component (`boards/arm/at32/at32f437-mini/src`)

## Overview
Board-level C implementation (`src`) for `at32f437-mini` (`arm/at32`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 18 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[at32f437-mini.h:at32_bringup]` Public declaration `at32_bringup()`
- `[at32f437-mini.h:at32_spidev_initialize]` Public declaration `at32_spidev_initialize()`
- `[at32f437-mini.h:at32_i2sdev_initialize]` Public declaration `at32_i2sdev_initialize()`
- `[at32f437-mini.h:at32_usbinitialize]` Public declaration `at32_usbinitialize()`
- `[at32f437-mini.h:at32_usbhost_initialize]` Public declaration `at32_usbhost_initialize()`
- `[at32f437-mini.h:at32_netinitialize]` Public declaration `at32_netinitialize()`
- `[at32f437-mini.h:at32_gpio_initialize]` Public declaration `at32_gpio_initialize()`
- `[at32f437-mini.h:at32_w25initialize]` Public declaration `at32_w25initialize()`
- `[at32f437-mini.h:at32_can_setup]` Public declaration `at32_can_setup()`
- `[at32f437-mini.h:at32_cansock_setup]` Public declaration `at32_cansock_setup()`
- `[at32f437-mini.h:at32_sdinitialize]` Public declaration `at32_sdinitialize()`
- `[at32f437-mini.h:at32_pwm_setup]` Public declaration `at32_pwm_setup()`
- `[at32f437-mini.h:at32_timer_driver_setup]` Public declaration `at32_timer_driver_setup()`
- `[at32f437-mini.h:at32_adc_setup]` Public declaration `at32_adc_setup()`
- `[at32f437-mini.h:at32_at24_automount]` Public declaration `at32_at24_automount()`
- `[at32f437-mini.h:board_userled_initialize]` Public declaration `board_userled_initialize()`
- `[at32f437-mini.h:at32_led_pminitialize]` Public declaration `at32_led_pminitialize()`
- `[at32f437-mini.h:HAVE_USBDEV]` Hardware/board configuration macros (`HAVE_USBDEV`, `HAVE_USBHOST`, `HAVE_USBMONITOR`, `HAVE_SDIO`, `HAVE_RTC_DRIVER`, `HAVE_W25` (+22 more))
- `[at32_adc.c:at32_adc_setup]` Public function `at32_adc_setup()`
- `[at32_at24.c:at32_at24_automount]` Public function `at32_at24_automount()`
- `[at32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[at32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[at32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[at32_boot.c:at32_boardinitialize]` Public function `at32_boardinitialize()`
- *(+31 additional symbols across 18 files)*

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_LEDS`, `CONFIG_AT32_ADC`, `CONFIG_AT32_CAN_CHARDRIVER`, `CONFIG_AT32_CAN_SOCKET`, `CONFIG_AT32_ETHMAC`, `CONFIG_AT32_OTGFS` (+8 more)
- `[at32f437-mini.h:#error]` Compile-time guard: `No HCI UART specified`
- `[at32_adc.c:at32_adc_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[at32_at24.c:at32_at24_automount]` Validates preconditions and returns `-ENODEV` on failure
- `[at32_bringup.c:at32_bringup]` Validates preconditions and returns `-ENOMEM` on failure
- `[at32_can.c:at32_can_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[at32_ethernet.c:DEBUGASSERT]` Requires `intf`
- `[at32_gpio.c:DEBUGASSERT]` Requires `at32gpint != NULL && at32gpint->callback != NULL`
- `[at32_gpio.c:DEBUGASSERT]` Requires `at32gpio != NULL && value != NULL`
- `[at32_gpio.c:DEBUGASSERT]` Requires `at32gpio->id < BOARD_NGPIOIN`
- `[at32_mmcsd.c:at32_sdinitialize]` Validates preconditions and returns `-ENODEV` on failure
- `[at32_pwm.c:at32_pwm_setup]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[at32_adc.c:at32_adc_setup]` Configures or drives hardware GPIO pins
- `[at32_adc.c:at32_adc_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`)
- `[at32_at24.c:at32_at24_automount]` Initializes/registers kernel devices or filesystems (`at24c_initialize()`, `at32_i2cbus_initialize()`, `nx_mount()`, `nxffs_initialize()`)
- `[at32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[at32_boot.c:at32_boardinitialize]` Initializes/registers kernel devices or filesystems (`at32_spidev_initialize()`, `board_autoled_initialize()`)
- `[at32_bringup.c:at32_bringup]` Initializes/registers kernel devices or filesystems (`at32_gpio_initialize()`, `at32_usbhost_initialize()`, `nx_mount()`, `rtc_initialize()`, `userled_lower_initialize()`)
- `[at32_can.c:at32_can_setup]` Initializes/registers kernel devices or filesystems (`can_register()`)
- `[at32_ethernet.c:at32_netinitialize]` Configures or drives hardware GPIO pins
- `[at32_ethernet.c:at32_netinitialize]` Modifies interrupt controller or critical-section state
- `[at32_gpio.c:at32_gpio_initialize]` Configures or drives hardware GPIO pins
- `[at32_gpio.c:at32_gpio_initialize]` Initializes/registers kernel devices or filesystems (`gpio_pin_register()`)
- `[at32_mmcsd.c:at32_sdinitialize]` Initializes/registers kernel devices or filesystems (`sdio_initialize()`)

## Verification
- Run: `./tools/configure.sh at32f437-mini:nsh && make`
