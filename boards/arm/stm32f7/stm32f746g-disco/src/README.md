# `stm32f746g-disco/src` Component (`boards/arm/stm32f7/stm32f746g-disco/src`)

## Overview
Board-level C implementation (`src`) for `stm32f746g-disco` (`arm/stm32f7`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 17 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[stm32f746g-disco.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[stm32f746g-disco.h:stm32_adc_setup]` Public declaration `stm32_adc_setup()`
- `[stm32f746g-disco.h:stm32_spidev_initialize]` Public declaration `stm32_spidev_initialize()`
- `[stm32f746g-disco.h:arch_sporadic_initialize]` Public declaration `arch_sporadic_initialize()`
- `[stm32f746g-disco.h:stm32_enablefmc]` Public declaration `stm32_enablefmc()`
- `[stm32f746g-disco.h:stm32_disablefmc]` Public declaration `stm32_disablefmc()`
- `[stm32f746g-disco.h:stm32_tsc_setup]` Public declaration `stm32_tsc_setup()`
- `[stm32f746g-disco.h:stm32_n25qxxx_setup]` Public declaration `stm32_n25qxxx_setup()`
- `[stm32f746g-disco.h:stm32_w25qxxx_setup]` Public declaration `stm32_w25qxxx_setup()`
- `[stm32f746g-disco.h:stm32_sdio_initialize]` Public declaration `stm32_sdio_initialize()`
- `[stm32f746g-disco.h:stm32_wm8994_initialize]` Public declaration `stm32_wm8994_initialize()`
- `[stm32f746g-disco.h:HAVE_USBDEV]` Hardware/board configuration macros (`HAVE_USBDEV`, `HAVE_USBHOST`, `HAVE_USBMONITOR`, `STM32_PROCFS_MOUNTPOINT`, `HAVE_SDIO`, `GPIO_LD1` (+11 more))
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
- `[stm32_extmem.c:stm32_enablefmc]` Public function `stm32_enablefmc()`
- *(+38 additional symbols across 17 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ADC`, `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_AUDIO_WM8994`, `CONFIG_INPUT_FT5X06` (+8 more)
- `[stm32_adc.c:#error]` Compile-time guard: `Only ADC3 channels are available on the arduino header of the board`
- `[stm32_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[stm32_extmem.c:#error]` Compile-time guard: `Required GPIO ports not enabled`
- `[stm32_sdmmc.c:stm32_sdio_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_spi.c:stm32_spidev_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_touchscreen.c:DEBUGASSERT]` Requires `minor == CONFIG_FT5X06_DEVMINOR`
- `[stm32_touchscreen.c:#error]` Compile-time guard: `FT5x06 support requires CONFIG_INPUT`
- `[stm32_touchscreen.c:#error]` Compile-time guard: `FT5x06 support requires CONFIG_STM32_I2C3`
- `[stm32_usb.c:DEBUGASSERT]` Requires `iface == 0`
- `[stm32_wm8994.c:DEBUGASSERT]` Requires `minor >= 0 && minor <= 25`

## Side Effects
- `[stm32_adc.c:stm32_adc_setup]` Configures or drives hardware GPIO pins
- `[stm32_adc.c:stm32_adc_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`, `stm32_adc_initialize()`)
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`arch_sporadic_initialize()`, `board_autoled_initialize()`, `stm32_spidev_initialize()`)
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`btn_lower_initialize()`, `fb_register()`, `nx_mount()`, `stm32_sdio_initialize()`, `stm32_usbhost_initialize()`)
- `[stm32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[stm32_extmem.c:stm32_enablefmc]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[stm32_extmem.c:stm32_enablefmc]` Configures or drives hardware GPIO pins
- `[stm32_lcd.c:up_fbinitialize]` Configures or drives hardware GPIO pins
- `[stm32_n25q.c:stm32_n25qxxx_setup]` Initializes/registers kernel devices or filesystems (`n25qxxx_initialize()`, `nx_mount()`, `nxffs_initialize()`, `stm32_qspi_initialize()`)
- `[stm32_sdmmc.c:stm32_sdio_initialize]` Configures or drives hardware GPIO pins
- `[stm32_sdmmc.c:stm32_sdio_initialize]` Initializes/registers kernel devices or filesystems (`sdio_initialize()`)

## Verification
- Run: `./tools/configure.sh stm32f746g-disco:nsh && make`
