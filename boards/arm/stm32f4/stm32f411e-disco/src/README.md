# `stm32f411e-disco/src` Component (`boards/arm/stm32f4/stm32f411e-disco/src`)

## Overview
Board-level C implementation (`src`) for `stm32f411e-disco` (`arm/stm32f4`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 7 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[stm32f411e-disco.h:stm32_spidev_initialize]` Public declaration `stm32_spidev_initialize()`
- `[stm32f411e-disco.h:stm32_usbinitialize]` Public declaration `stm32_usbinitialize()`
- `[stm32f411e-disco.h:stm32_usbhost_initialize]` Public declaration `stm32_usbhost_initialize()`
- `[stm32f411e-disco.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[stm32f411e-disco.h:GPIO_LD3]` Hardware/board configuration macros (`GPIO_LD3`, `GPIO_LD4`, `GPIO_LD5`, `GPIO_LD6`, `MIN_IRQBUTTON`, `MAX_IRQBUTTON` (+9 more))
- `[stm32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[stm32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_bringup.c:stm32_bringup]` Public function `stm32_bringup()`
- `[stm32_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[stm32_buttons.c:board_buttons]` Public function `board_buttons()`
- `[stm32_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[stm32_usb.c:stm32_usbinitialize]` Public function `stm32_usbinitialize()`
- `[stm32_usb.c:stm32_usbhost_initialize]` Public function `stm32_usbhost_initialize()`
- `[stm32_usb.c:stm32_usbhost_vbusdrive]` Public function `stm32_usbhost_vbusdrive()`
- `[stm32_usb.c:stm32_setup_overcurrent]` Public function `stm32_setup_overcurrent()`
- `[stm32_usb.c:stm32_usbsuspend]` Public function `stm32_usbsuspend()`
- `[stm32_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[stm32_userleds.c:board_userled]` Public function `board_userled()`
- `[stm32_userleds.c:board_userled_all]` Public function `board_userled_all()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_STM32_OTGFS`
- `[stm32_buttons.c:#error]` Compile-time guard: `The NuttX Buttons Driver depends on IRQ support to work!\n`
- `[stm32_usb.c:DEBUGASSERT]` Requires `iface == 0`

## Side Effects
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `stm32_spidev_initialize()`)
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`btn_lower_initialize()`, `nx_mount()`, `stm32_usbhost_initialize()`, `userled_lower_initialize()`)
- `[stm32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[stm32_usb.c:stm32_usbinitialize]` Configures or drives hardware GPIO pins
- `[stm32_usb.c:stm32_usbinitialize]` Initializes/registers kernel devices or filesystems (`stm32_otgfshost_initialize()`, `usbhost_cdcacm_initialize()`, `usbhost_hub_initialize()`, `usbhost_msc_initialize()`)
- `[stm32_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh stm32f411e-disco:nsh && make`
