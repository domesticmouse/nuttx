# `olimex-stm32-p407/src` Component (`boards/arm/stm32f4/olimex-stm32-p407/src`)

## Overview
Board-level C implementation (`src`) for `olimex-stm32-p407` (`arm/stm32f4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 14 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[olimex-stm32-p407.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[olimex-stm32-p407.h:stm32_spidev_initialize]` Public declaration `stm32_spidev_initialize()`
- `[olimex-stm32-p407.h:stm32_stram_configure]` Public declaration `stm32_stram_configure()`
- `[olimex-stm32-p407.h:stm32_usb_configure]` Public declaration `stm32_usb_configure()`
- `[olimex-stm32-p407.h:stm32_usbhost_setup]` Public declaration `stm32_usbhost_setup()`
- `[olimex-stm32-p407.h:stm32_adc_setup]` Public declaration `stm32_adc_setup()`
- `[olimex-stm32-p407.h:stm32_can_setup]` Public declaration `stm32_can_setup()`
- `[olimex-stm32-p407.h:stm32_cs4344_initialize]` Public declaration `stm32_cs4344_initialize()`
- `[olimex-stm32-p407.h:stm32_djoy_initialize]` Public declaration `stm32_djoy_initialize()`
- `[olimex-stm32-p407.h:HAVE_MMCSD]` Hardware/board configuration macros (`HAVE_MMCSD`, `HAVE_USBDEV`, `HAVE_USBHOST`, `HAVE_USBMONITOR`, `HAVE_ELF`, `HAVE_MODSYMS` (+26 more))
- `[stm32_adc.c:stm32_adc_setup]` Public function `stm32_adc_setup()`
- `[stm32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[stm32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_bringup.c:stm32_bringup]` Public function `stm32_bringup()`
- `[stm32_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[stm32_buttons.c:board_buttons]` Public function `board_buttons()`
- `[stm32_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[stm32_can.c:stm32_can_setup]` Public function `stm32_can_setup()`
- `[stm32_cs4344.c:stm32_cs4344_initialize]` Public function `stm32_cs4344_initialize()`
- `[stm32_djoystick.c:stm32_djoy_initialize]` Public function `stm32_djoy_initialize()`
- *(+22 additional symbols across 14 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ADC`, `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_AUDIO_CS4344`, `CONFIG_INPUT_DJOYSTICK` (+3 more)
- `[olimex-stm32-p407.h:#error]` Compile-time guard: `Only one MMC/SD slot`
- `[stm32_adc.c:stm32_adc_setup]` Validates preconditions and returns `-ENODEV`, `-ENOSYS` on failure
- `[stm32_bringup.c:stm32_bringup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[stm32_can.c:stm32_can_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_cs4344.c:DEBUGASSERT]` Requires `minor >= 0 && minor <= 25`
- `[stm32_djoystick.c:DEBUGASSERT]` Requires `g_djoyhandler`
- `[stm32_spi.c:stm32_spidev_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_sram.c:#error]` Compile-time guard: `Required GPIO ports not enabled`
- `[stm32_sram.c:#error]` Compile-time guard: `USART3 and USART6 conflict with use of SRAM`
- `[stm32_st7735.c:board_lcd_initialize]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[stm32_adc.c:stm32_adc_setup]` Configures or drives hardware GPIO pins
- `[stm32_adc.c:stm32_adc_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`)
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `board_button_initialize()`, `stm32_spidev_initialize()`)
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`board_dhtxx_initialize()`, `btn_lower_initialize()`, `nx_mount()`, `sdio_initialize()`, `stm32_cs4344_initialize()`)
- `[stm32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[stm32_can.c:stm32_can_setup]` Initializes/registers kernel devices or filesystems (`can_register()`)
- `[stm32_cs4344.c:stm32_cs4344_initialize]` Initializes/registers kernel devices or filesystems (`audio_register()`, `cs4344_initialize()`, `pcm_decode_initialize()`, `stm32_i2sbus_initialize()`)
- `[stm32_djoystick.c:stm32_djoy_initialize]` Configures or drives hardware GPIO pins
- `[stm32_djoystick.c:stm32_djoy_initialize]` Initializes/registers kernel devices or filesystems (`djoy_register()`)
- `[stm32_djoystick.c:stm32_djoy_initialize]` Modifies interrupt controller or critical-section state
- `[stm32_spi.c:stm32_spidev_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh olimex-stm32-p407:nsh && make`
