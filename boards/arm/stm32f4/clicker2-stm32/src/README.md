# `clicker2-stm32/src` Component (`boards/arm/stm32f4/clicker2-stm32/src`)

## Overview
Board-level C implementation (`src`) for `clicker2-stm32` (`arm/stm32f4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 14 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[clicker2-stm32.h:stm32_spidev_initialize]` Public declaration `stm32_spidev_initialize()`
- `[clicker2-stm32.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[clicker2-stm32.h:stm32_usb_configure]` Public declaration `stm32_usb_configure()`
- `[clicker2-stm32.h:stm32_adc_setup]` Public declaration `stm32_adc_setup()`
- `[clicker2-stm32.h:stm32_can_setup]` Public declaration `stm32_can_setup()`
- `[clicker2-stm32.h:stm32_mrf24j40_initialize]` Public declaration `stm32_mrf24j40_initialize()`
- `[clicker2-stm32.h:stm32_xbee_initialize]` Public declaration `stm32_xbee_initialize()`
- `[clicker2-stm32.h:stm32_mmcsd_initialize]` Public declaration `stm32_mmcsd_initialize()`
- `[clicker2-stm32.h:stm32_cardinserted]` Public declaration `stm32_cardinserted()`
- `[clicker2-stm32.h:stm32_automount_initialize]` Public declaration `stm32_automount_initialize()`
- `[clicker2-stm32.h:stm32_automount_event]` Public declaration `stm32_automount_event()`
- `[clicker2-stm32.h:HAVE_USBDEV]` Hardware/board configuration macros (`HAVE_USBDEV`, `HAVE_USBMONITOR`, `HAVE_MMCSD`, `HAVE_AUTOMOUNTER`, `MB1_MMCSD_SLOTNO`, `MB2_MMCSD_SLOTNO` (+15 more))
- `[stm32_adc.c:stm32_adc_setup]` Public function `stm32_adc_setup()`
- `[stm32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[stm32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_automount.c:stm32_automount_initialize]` Public function `stm32_automount_initialize()`
- `[stm32_automount.c:stm32_automount_event]` Public function `stm32_automount_event()`
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_bringup.c:stm32_bringup]` Public function `stm32_bringup()`
- `[stm32_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[stm32_buttons.c:board_buttons]` Public function `board_buttons()`
- *(+23 additional symbols across 14 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ADC`, `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_FS_AUTOMOUNTER`, `CONFIG_IEEE802154_MRF24J40` (+4 more)
- `[stm32_adc.c:stm32_adc_setup]` Validates preconditions and returns `-ENODEV`, `-ENOSYS` on failure
- `[stm32_automount.c:DEBUGASSERT]` Requires `config && config->state`
- `[stm32_can.c:stm32_can_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_mmcsd.c:#error]` Compile-time guard: `Only the Mikroe uSD click boards are supported`
- `[stm32_mmcsd.c:#error]` Compile-time guard: `Mountpoints are required for MMCSD support`
- `[stm32_mrf24j40.c:DEBUGASSERT]` Requires `priv != NULL`
- `[stm32_mrf24j40.c:DEBUGASSERT]` Requires `priv != NULL && (priv->handler != NULL || !state)`
- `[stm32_mrf24j40.c:#error]` Compile-time guard: `Wireless support requires CONFIG_DRIVERS_WIRELESS`
- `[stm32_mrf24j40.c:#error]` Compile-time guard: `Only the Mikroe BEE board is supported`
- `[stm32_spi.c:stm32_spidev_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_xbee.c:DEBUGASSERT]` Requires `priv != NULL`

## Side Effects
- `[stm32_adc.c:stm32_adc_setup]` Configures or drives hardware GPIO pins
- `[stm32_adc.c:stm32_adc_setup]` Initializes/registers kernel devices or filesystems (`adc_register()`)
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_automount.c:stm32_automount_initialize]` Initializes/registers kernel devices or filesystems (`automount_initialize()`)
- `[stm32_automount.c:stm32_automount_initialize]` Modifies interrupt controller or critical-section state
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `board_button_initialize()`, `stm32_spidev_initialize()`)
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`btn_lower_initialize()`, `nx_mount()`, `stm32_automount_initialize()`, `stm32_mmcsd_initialize()`, `stm32_mrf24j40_initialize()`)
- `[stm32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[stm32_can.c:stm32_can_setup]` Initializes/registers kernel devices or filesystems (`can_register()`)
- `[stm32_mmcsd.c:stm32_mmcsd_initialize]` Configures or drives hardware GPIO pins
- `[stm32_mmcsd.c:stm32_mmcsd_initialize]` Initializes/registers kernel devices or filesystems (`stm32_spibus_initialize()`)
- `[stm32_mrf24j40.c:stm32_mrf24j40_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh clicker2-stm32:nsh && make`
