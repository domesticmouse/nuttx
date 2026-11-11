# `stm32f4discovery/src` Component (`boards/arm/stm32f4/stm32f4discovery/src`)

## Overview
Board-level C implementation (`src`) for `stm32f4discovery` (`arm/stm32f4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 43 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[stm32f4discovery.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[stm32f4discovery.h:stm32_spidev_initialize]` Public declaration `stm32_spidev_initialize()`
- `[stm32f4discovery.h:stm32_i2sdev_initialize]` Public declaration `stm32_i2sdev_initialize()`
- `[stm32f4discovery.h:stm32_bh1750initialize]` Public declaration `stm32_bh1750initialize()`
- `[stm32f4discovery.h:stm32_lpwaninitialize]` Public declaration `stm32_lpwaninitialize()`
- `[stm32f4discovery.h:stm32_mmcsd_initialize]` Public declaration `stm32_mmcsd_initialize()`
- `[stm32f4discovery.h:nunchuck_initialize]` Public declaration `nunchuck_initialize()`
- `[stm32f4discovery.h:stm32_max7219init]` Public declaration `stm32_max7219init()`
- `[stm32f4discovery.h:stm32_st7032init]` Public declaration `stm32_st7032init()`
- `[stm32f4discovery.h:stm32_usbinitialize]` Public declaration `stm32_usbinitialize()`
- `[stm32f4discovery.h:stm32_usbhost_initialize]` Public declaration `stm32_usbhost_initialize()`
- `[stm32f4discovery.h:stm32_pwm_setup]` Public declaration `stm32_pwm_setup()`
- `[stm32f4discovery.h:stm32_capture_setup]` Public declaration `stm32_capture_setup()`
- `[stm32f4discovery.h:stm32_can_setup]` Public declaration `stm32_can_setup()`
- `[stm32f4discovery.h:stm32_extmemgpios]` Public declaration `stm32_extmemgpios()`
- `[stm32f4discovery.h:stm32_extmemaddr]` Public declaration `stm32_extmemaddr()`
- `[stm32f4discovery.h:stm32_extmemdata]` Public declaration `stm32_extmemdata()`
- `[stm32f4discovery.h:stm32_led_pminitialize]` Public declaration `stm32_led_pminitialize()`
- `[stm32f4discovery.h:stm32_pm_buttons]` Public declaration `stm32_pm_buttons()`
- `[stm32f4discovery.h:stm32_sdio_initialize]` Public declaration `stm32_sdio_initialize()`
- `[stm32f4discovery.h:stm32_netinitialize]` Public declaration `stm32_netinitialize()`
- `[stm32f4discovery.h:stm32_zerocross_initialize]` Public declaration `stm32_zerocross_initialize()`
- `[stm32f4discovery.h:stm32_max31855initialize]` Public declaration `stm32_max31855initialize()`
- *(+92 additional symbols across 43 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ADC_HX711`, `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_CUSTOM_PMINIT`, `CONFIG_ARCH_IDLE_CUSTOM`, `CONFIG_ARCH_LEDS` (+34 more)
- `[stm32f4discovery.h:#error]` Compile-time guard: `No HCI UART specified`
- `[stm32_apa102.c:board_lcd_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_bringup.c:stm32_bringup]` Validates preconditions and returns `-ENOMEM` on failure
- `[stm32_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[stm32_can.c:stm32_can_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_capture.c:stm32_capture_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_composite.c:DEBUGASSERT]` Requires `g_mschandle == NULL`
- `[stm32_composite.c:DEBUGASSERT]` Requires `epin < STM32_NENDPOINTS`
- `[stm32_composite.c:DEBUGASSERT]` Requires `epout < STM32_NENDPOINTS`
- `[stm32_cs43l22.c:DEBUGASSERT]` Requires `minor >= 0 && minor <= 25`
- `[stm32_djoystick.c:DEBUGASSERT]` Requires `g_djoyhandler`

## Side Effects
- `[stm32_apa102.c:board_lcd_initialize]` Initializes/registers kernel devices or filesystems (`apa102_initialize()`, `stm32_spibus_initialize()`)
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `stm32_spidev_initialize()`)
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`board_apds9960_initialize()`, `board_bh1750_initialize()`, `board_bmp180_initialize()`, `board_ds1307_initialize()`, `board_kmatrix_i2c_initialize()`)
- `[stm32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[stm32_can.c:stm32_can_setup]` Initializes/registers kernel devices or filesystems (`can_register()`)
- `[stm32_capture.c:stm32_capture_setup]` Initializes/registers kernel devices or filesystems (`cap_register()`, `stm32_cap_initialize()`)
- `[stm32_composite.c:board_composite_initialize]` Initializes/registers kernel devices or filesystems (`composite_initialize()`)
- `[stm32_cs43l22.c:stm32_cs43l22_initialize]` Configures or drives hardware GPIO pins
- `[stm32_cs43l22.c:stm32_cs43l22_initialize]` Initializes/registers kernel devices or filesystems (`audio_register()`, `cs43l22_initialize()`, `pcm_decode_initialize()`, `stm32_i2cbus_initialize()`, `stm32_i2sbus_initialize()`)
- `[stm32_cs43l22.c:stm32_cs43l22_initialize]` Modifies interrupt controller or critical-section state
- `[stm32_djoystick.c:stm32_djoy_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh stm32f4discovery:nsh && make`
