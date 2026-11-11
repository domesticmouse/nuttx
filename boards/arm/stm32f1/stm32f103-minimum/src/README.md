# `stm32f103-minimum/src` Component (`boards/arm/stm32f1/stm32f103-minimum/src`)

## Overview
Board-level C implementation (`src`) for `stm32f103-minimum` (`arm/stm32f1`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 26 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[stm32f103_minimum.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[stm32f103_minimum.h:stm32_gpio_initialize]` Public declaration `stm32_gpio_initialize()`
- `[stm32f103_minimum.h:stm32_adc_setup]` Public declaration `stm32_adc_setup()`
- `[stm32f103_minimum.h:stm32_spidev_initialize]` Public declaration `stm32_spidev_initialize()`
- `[stm32f103_minimum.h:stm32_mmcsd_initialize]` Public declaration `stm32_mmcsd_initialize()`
- `[stm32f103_minimum.h:stm32_w25initialize]` Public declaration `stm32_w25initialize()`
- `[stm32f103_minimum.h:stm32_rgbled_setup]` Public declaration `stm32_rgbled_setup()`
- `[stm32f103_minimum.h:stm32_mcp2515initialize]` Public declaration `stm32_mcp2515initialize()`
- `[stm32f103_minimum.h:stm32_usbinitialize]` Public declaration `stm32_usbinitialize()`
- `[stm32f103_minimum.h:stm32_pwm_setup]` Public declaration `stm32_pwm_setup()`
- `[stm32f103_minimum.h:stm32_max3421e_setup]` Public declaration `stm32_max3421e_setup()`
- `[stm32f103_minimum.h:stm32_hyt271initialize]` Public declaration `stm32_hyt271initialize()`
- `[stm32f103_minimum.h:stm32_ds18b20initialize]` Public declaration `stm32_ds18b20initialize()`
- `[stm32f103_minimum.h:stm32_can_setup]` Public declaration `stm32_can_setup()`
- `[stm32f103_minimum.h:stm32_cansock_setup]` Public declaration `stm32_cansock_setup()`
- `[stm32f103_minimum.h:HAVE_AT24]` Hardware/board configuration macros (`HAVE_AT24`, `AT24_I2C_BUS`, `AT24_MINOR`, `STM32_PROCFS_MOUNTPOINT`, `GPIO_LED1`, `GPIO_BTN_USER1` (+35 more))
- `[stm32_adc.c:stm32_adc_setup]` Public function `stm32_adc_setup()`
- `[stm32_at24.c:stm32_at24_automount]` Public function `stm32_at24_automount()`
- `[stm32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[stm32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- *(+42 additional symbols across 26 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ADC`, `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_CAN_MCP2515`, `CONFIG_DEV_GPIO` (+18 more)
- `[stm32_adc.c:stm32_adc_setup]` Validates preconditions and returns `-ENODEV`, `-ENOSYS` on failure
- `[stm32_at24.c:stm32_at24_automount]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_buttons.c:#error]` Compile-time guard: `The NuttX Buttons Driver depends on IRQ support to work!\n`
- `[stm32_can.c:stm32_can_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_ds18b20.c:DEBUGASSERT]` Requires `ret > maxslaves`
- `[stm32_ds18b20.c:#error]` Compile-time guard: `Definition BOARD_DS18B20_NBUS is missing`
- `[stm32_ds18b20.c:#error]` Compile-time guard: `Definition BOARD_DS18B20_NSLAVES is missing`
- `[stm32_gpio.c:DEBUGASSERT]` Requires `stm32gpint != NULL && stm32gpint->callback != NULL`
- `[stm32_gpio.c:DEBUGASSERT]` Requires `stm32gpio != NULL && value != NULL`
- `[stm32_gpio.c:DEBUGASSERT]` Requires `stm32gpio->id < BOARD_NGPIOIN`
- `[stm32_hyt271.c:#error]` Compile-time guard: `Configuration BOARD_HYT271_NBUS missing`

## Side Effects
- `[stm32_adc.c:stm32_adc_setup]` Configures or drives hardware GPIO pins
- `[stm32_adc.c:stm32_adc_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`)
- `[stm32_at24.c:stm32_at24_automount]` Initializes/registers kernel devices or filesystems (`at24c_initialize()`, `nx_mount()`, `nxffs_initialize()`, `stm32_i2cbus_initialize()`)
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `stm32_spidev_initialize()`)
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`board_apa102_initialize()`, `board_apds9960_initialize()`, `board_bmp180_initialize()`, `board_hcsr04_initialize()`, `board_lm75_initialize()`)
- `[stm32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[stm32_can.c:stm32_can_setup]` Initializes/registers kernel devices or filesystems (`can_register()`)
- `[stm32_ds18b20.c:stm32_ds18b20initialize]` Initializes/registers kernel devices or filesystems (`ds18b20_register()`, `onewire_initialize()`)
- `[stm32_gpio.c:stm32_gpio_initialize]` Configures or drives hardware GPIO pins
- `[stm32_gpio.c:stm32_gpio_initialize]` Initializes/registers kernel devices or filesystems (`gpio_pin_register()`)
- `[stm32_hyt271.c:stm32_hyt271initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh stm32f103-minimum:nsh && make`
