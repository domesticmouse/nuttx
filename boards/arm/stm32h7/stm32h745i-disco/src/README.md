# `stm32h745i-disco/src` Component (`boards/arm/stm32h7/stm32h745i-disco/src`)

## Overview
Board-level C implementation (`src`) for `stm32h745i-disco` (`arm/stm32h7`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 9 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[stm32h745i_disco.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[stm32h745i_disco.h:stm32_usbinitialize]` Public declaration `stm32_usbinitialize()`
- `[stm32h745i_disco.h:stm32_usbhost_initialize]` Public declaration `stm32_usbhost_initialize()`
- `[stm32h745i_disco.h:stm32_tsc_setup]` Public declaration `stm32_tsc_setup()`
- `[stm32h745i_disco.h:HAVE_USBDEV]` Hardware/board configuration macros (`HAVE_USBDEV`, `HAVE_USBHOST`, `HAVE_USBMONITOR`, `GPIO_LD1`, `GPIO_LD2`, `GPIO_LD3` (+19 more))
- `[stm32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[stm32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_bringup.c:rpmsg_serialinit]` Public function `rpmsg_serialinit()`
- `[stm32_bringup.c:stm32_bringup]` Public function `stm32_bringup()`
- `[stm32_ft5x06.c:stm32_tsc_setup]` Public function `stm32_tsc_setup()`
- `[stm32_lcd.c:up_fbinitialize]` Public function `up_fbinitialize()`
- `[stm32_lcd.c:up_fbgetvplane]` Public function `up_fbgetvplane()`
- `[stm32_lcd.c:up_fbuninitialize]` Public function `up_fbuninitialize()`
- `[stm32_ostest.c:arch_getfpu]` Public function `arch_getfpu()`
- `[stm32_ostest.c:arch_cmpfpu]` Public function `arch_cmpfpu()`
- `[stm32_usb.c:stm32_usbinitialize]` Public function `stm32_usbinitialize()`
- `[stm32_usb.c:stm32_usbhost_initialize]` Public function `stm32_usbhost_initialize()`
- `[stm32_usb.c:stm32_usbhost_vbusdrive]` Public function `stm32_usbhost_vbusdrive()`
- `[stm32_usb.c:stm32_setup_overcurrent]` Public function `stm32_setup_overcurrent()`
- `[stm32_usb.c:stm32_usbsuspend]` Public function `stm32_usbsuspend()`
- *(+3 additional symbols across 9 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_LEDS`, `CONFIG_INPUT_FT5X06`, `CONFIG_STM32_LTDC`, `CONFIG_STM32_OTGFS`, `CONFIG_TESTING_OSTEST`
- `[stm32_ft5x06.c:DEBUGASSERT]` Requires `minor == CONFIG_FT5X06_DEVMINOR`
- `[stm32_ft5x06.c:#error]` Compile-time guard: `FT5x06 support requires CONFIG_INPUT`
- `[stm32_ft5x06.c:#error]` Compile-time guard: `FT5x06 support requires CONFIG_STM32_I2C4`
- `[stm32_ostest.c:#error]` Compile-time guard: `CONFIG_TESTING_OSTEST_FPUSIZE has the wrong size`
- `[stm32_usb.c:DEBUGASSERT]` Requires `iface == 0`

## Side Effects
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[stm32_bringup.c:rpmsg_serialinit]` Configures or drives hardware GPIO pins
- `[stm32_bringup.c:rpmsg_serialinit]` Initializes/registers kernel devices or filesystems (`fb_register()`, `nx_mount()`, `rammtd_initialize()`, `stm32_usbhost_initialize()`, `userled_lower_initialize()`)
- `[stm32_ft5x06.c:stm32_tsc_setup]` Configures or drives hardware GPIO pins
- `[stm32_ft5x06.c:stm32_tsc_setup]` Initializes/registers kernel devices or filesystems (`ft5x06_register()`, `stm32_i2cbus_initialize()`)
- `[stm32_ft5x06.c:stm32_tsc_setup]` Modifies interrupt controller or critical-section state
- `[stm32_lcd.c:up_fbinitialize]` Configures or drives hardware GPIO pins
- `[stm32_ostest.c:arch_getfpu]` Modifies interrupt controller or critical-section state
- `[stm32_usb.c:stm32_usbinitialize]` Configures or drives hardware GPIO pins
- `[stm32_usb.c:stm32_usbinitialize]` Initializes/registers kernel devices or filesystems (`stm32_otgfshost_initialize()`, `usbhost_cdcacm_initialize()`, `usbhost_hub_initialize()`, `usbhost_msc_initialize()`)
- `[stm32_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh stm32h745i-disco:nsh && make`
