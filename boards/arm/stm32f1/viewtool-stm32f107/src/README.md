# `viewtool-stm32f107/src` Component (`boards/arm/stm32f1/viewtool-stm32f107/src`)

## Overview
Board-level C implementation (`src`) for `viewtool-stm32f107` (`arm/stm32f1`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 15 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[viewtool_stm32f107.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[viewtool_stm32f107.h:stm32_spidev_initialize]` Public declaration `stm32_spidev_initialize()`
- `[viewtool_stm32f107.h:stm32_led_initialize]` Public declaration `stm32_led_initialize()`
- `[viewtool_stm32f107.h:stm32_usbdev_initialize]` Public declaration `stm32_usbdev_initialize()`
- `[viewtool_stm32f107.h:stm32_tsc_setup]` Public declaration `stm32_tsc_setup()`
- `[viewtool_stm32f107.h:stm32_sdinitialize]` Public declaration `stm32_sdinitialize()`
- `[viewtool_stm32f107.h:stm32_can_setup]` Public declaration `stm32_can_setup()`
- `[viewtool_stm32f107.h:stm32_mpl115ainitialize]` Public declaration `stm32_mpl115ainitialize()`
- `[viewtool_stm32f107.h:stm32_ft80x_setup]` Public declaration `stm32_ft80x_setup()`
- `[viewtool_stm32f107.h:stm32_max3421e_setup]` Public declaration `stm32_max3421e_setup()`
- `[viewtool_stm32f107.h:HAVE_USBDEV]` Hardware/board configuration macros (`HAVE_USBDEV`, `HAVE_MMCSD`, `HAVE_RTC_DRIVER`, `VIEWTOOL_MMCSD_SLOTNO`, `STM32_PROCFS_MOUNTPOINT`, `GPIO_LED1` (+24 more))
- `[stm32_ads7843e.c:stm32_tsc_setup]` Public function `stm32_tsc_setup()`
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_bringup.c:stm32_bringup]` Public function `stm32_bringup()`
- `[stm32_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[stm32_buttons.c:board_buttons]` Public function `board_buttons()`
- `[stm32_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[stm32_can.c:stm32_can_setup]` Public function `stm32_can_setup()`
- `[stm32_ft80x.c:stm32_ft80x_setup]` Public function `stm32_ft80x_setup()`
- `[stm32_highpri.c:tim6_handler]` Public function `tim6_handler()`
- `[stm32_highpri.c:highpri_main]` Public function `highpri_main()`
- `[stm32_leds.c:stm32_led_initialize]` Public function `stm32_led_initialize()`
- *(+21 additional symbols across 15 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_INPUT_ADS7843E`, `CONFIG_LCD_SSD1289`, `CONFIG_MMCSD`, `CONFIG_STM32_CAN_CHARDRIVER` (+8 more)
- `[viewtool_stm32f107.h:#error]` Compile-time guard: `Unknown chip on Viewtool board`
- `[stm32_ads7843e.c:DEBUGASSERT]` Requires `minor == 0`
- `[stm32_ads7843e.c:#error]` Compile-time guard: `CONFIG_STM32_SPI2 is required for touchscreen support`
- `[stm32_bringup.c:#error]` Compile-time guard: `Only one MMC/SD slot: VIEWTOOL_MMCSD_SLOTNO`
- `[stm32_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[stm32_can.c:stm32_can_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_ft80x.c:stm32_ft80x_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_highpri.c:#error]` Compile-time guard: `CONFIG_ARCH_HIPRI_INTERRUPT is required`
- `[stm32_highpri.c:#error]` Compile-time guard: `CONFIG_ARCH_RAMVECTORS is required`
- `[stm32_max3421e.c:stm32_max3421e_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_mmcsd.c:stm32_sdinitialize]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[stm32_ads7843e.c:stm32_tsc_setup]` Configures or drives hardware GPIO pins
- `[stm32_ads7843e.c:stm32_tsc_setup]` Initializes/registers kernel devices or filesystems (`ads7843e_register()`, `stm32_spibus_initialize()`)
- `[stm32_ads7843e.c:stm32_tsc_setup]` Modifies interrupt controller or critical-section state
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`stm32_led_initialize()`, `stm32_spidev_initialize()`, `stm32_usbdev_initialize()`)
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`board_mpl115a_initialize()`, `nx_mount()`, `rtc_driver_initialize()`, `rtc_initialize()`)
- `[stm32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[stm32_can.c:stm32_can_setup]` Initializes/registers kernel devices or filesystems (`can_register()`)
- `[stm32_ft80x.c:stm32_ft80x_setup]` Configures or drives hardware GPIO pins
- `[stm32_ft80x.c:stm32_ft80x_setup]` Initializes/registers kernel devices or filesystems (`ft80x_register()`, `stm32_spibus_initialize()`)
- `[stm32_ft80x.c:stm32_ft80x_setup]` Modifies interrupt controller or critical-section state
- `[stm32_highpri.c:tim6_handler]` Modifies interrupt controller or critical-section state
- `[stm32_leds.c:stm32_led_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh viewtool-stm32f107:nsh && make`
