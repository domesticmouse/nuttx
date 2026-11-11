# `stm32butterfly2/src` Component (`boards/arm/stm32f1/stm32butterfly2/src`)

## Overview
Board-level C implementation (`src`) for `stm32butterfly2` (`arm/stm32f1`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 10 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[stm32_butterfly2.h:stm32_led_initialize]` Public declaration `stm32_led_initialize()`
- `[stm32_butterfly2.h:stm32_spidev_initialize]` Public declaration `stm32_spidev_initialize()`
- `[stm32_butterfly2.h:stm32_mmcsd_initialize]` Public declaration `stm32_mmcsd_initialize()`
- `[stm32_butterfly2.h:stm32_usb_initialize]` Public declaration `stm32_usb_initialize()`
- `[stm32_butterfly2.h:stm32_usbhost_initialize]` Public declaration `stm32_usbhost_initialize()`
- `[stm32_butterfly2.h:stm32_adc_setup]` Public declaration `stm32_adc_setup()`
- `[stm32_butterfly2.h:GPIO_SD_CS]` Hardware/board configuration macros (`GPIO_SD_CS`, `GPIO_SD_CD`, `GPIO_OTGFS_PWRON`)
- `[stm32_adc.c:stm32_adc_setup]` Public function `stm32_adc_setup()`
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[stm32_buttons.c:board_buttons]` Public function `board_buttons()`
- `[stm32_leds.c:stm32_led_initialize]` Public function `stm32_led_initialize()`
- `[stm32_leds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_leds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_leds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[stm32_leds.c:board_userled]` Public function `board_userled()`
- `[stm32_leds.c:board_userled_all]` Public function `board_userled_all()`
- `[stm32_mmcsd.c:stm32_spi1register]` Public function `stm32_spi1register()`
- `[stm32_mmcsd.c:stm32_mmcsd_initialize]` Public function `stm32_mmcsd_initialize()`
- `[stm32_spi.c:stm32_spidev_initialize]` Public function `stm32_spidev_initialize()`
- `[stm32_spi.c:stm32_spi1select]` Public function `stm32_spi1select()`
- `[stm32_spi.c:stm32_spi1status]` Public function `stm32_spi1status()`
- *(+4 additional symbols across 10 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_MMCSD`, `CONFIG_STM32_ADC`, `CONFIG_STM32_OTGFS`, `CONFIG_STM32_SPI1` (+2 more)
- `[stm32_adc.c:stm32_adc_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_mmcsd.c:#error]` Compile-time guard: `SD driver requires CONFIG_STM32_SPI1 to be enabled`
- `[stm32_mmcsd.c:#error]` Compile-time guard: `SD driver requires CONFIG_DISABLE_MOUNTPOINT to be disabled`
- `[stm32_usbdev.c:#error]` Compile-time guard: `CONFIG_USBDEV requires CONFIG_STM32_OTGFS to be enabled`
- `[stm32_usbdev.c:#error]` Compile-time guard: `CONFIG_USBDEV cannot be set alongside CONFIG_USBHOST`
- `[stm32_usbhost.c:#error]` Compile-time guard: `CONFIG_USBHOST requires CONFIG_STM32_OTGFS to be enabled`
- `[stm32_usbhost.c:#error]` Compile-time guard: `CONFIG_USBHOST cannot be set alongside CONFIG_USBDEV`

## Side Effects
- `[stm32_adc.c:stm32_adc_setup]` Configures or drives hardware GPIO pins
- `[stm32_adc.c:stm32_adc_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`)
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`stm32_led_initialize()`, `stm32_mmcsd_initialize()`, `stm32_spidev_initialize()`, `stm32_usb_initialize()`, `stm32_usbhost_initialize()`)
- `[stm32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[stm32_leds.c:stm32_led_initialize]` Configures or drives hardware GPIO pins
- `[stm32_mmcsd.c:stm32_spi1register]` Initializes/registers kernel devices or filesystems (`stm32_spibus_initialize()`)
- `[stm32_spi.c:stm32_spidev_initialize]` Configures or drives hardware GPIO pins
- `[stm32_usb.c:stm32_usb_initialize]` Configures or drives hardware GPIO pins
- `[stm32_usbhost.c:stm32_usbhost_initialize]` Configures or drives hardware GPIO pins
- `[stm32_usbhost.c:stm32_usbhost_initialize]` Initializes/registers kernel devices or filesystems (`stm32_otgfshost_initialize()`, `usbhost_cdacm_initialize()`, `usbhost_hub_initialize()`, `usbhost_msc_initialize()`)

## Verification
- Run: `./tools/configure.sh stm32butterfly2:nsh && make`
