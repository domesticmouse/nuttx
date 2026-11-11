# `olimex-lpc1766stk/src` Component (`boards/arm/lpc17xx_40xx/olimex-lpc1766stk/src`)

## Overview
Board-level C implementation (`src`) for `olimex-lpc1766stk` (`arm/lpc17xx_40xx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[lpc1766stk.h:lpc17_40_bringup]` Public declaration `lpc17_40_bringup()`
- `[lpc1766stk.h:lpc1766stk_sspdev_initialize]` Public declaration `lpc1766stk_sspdev_initialize()`
- `[lpc1766stk.h:lpc1766stk_can_setup]` Public declaration `lpc1766stk_can_setup()`
- `[lpc1766stk.h:LPC1766STK_LED1]` Hardware/board configuration macros (`LPC1766STK_LED1`, `LPC1766STK_LED2`, `LPC1766STK_BUT1`, `LPC1766STK_BUT2`, `LPC1766STK_WAKEUP`, `LPC1766STK_BUT1_IRQ` (+20 more))
- `[lpc17_40_boot.c:lpc17_40_boardinitialize]` Public function `lpc17_40_boardinitialize()`
- `[lpc17_40_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[lpc17_40_bringup.c:lpc17_40_bringup]` Public function `lpc17_40_bringup()`
- `[lpc17_40_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[lpc17_40_buttons.c:board_buttons]` Public function `board_buttons()`
- `[lpc17_40_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[lpc17_40_can.c:lpc1766stk_can_setup]` Public function `lpc1766stk_can_setup()`
- `[lpc17_40_leds.c:board_userled]` Public function `board_userled()`
- `[lpc17_40_leds.c:board_userled_all]` Public function `board_userled_all()`
- `[lpc17_40_leds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[lpc17_40_leds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[lpc17_40_ssp.c:lpc1766stk_sspdev_initialize]` Public function `lpc1766stk_sspdev_initialize()`
- `[lpc17_40_ssp.c:lpc17_40_ssp0select]` Public function `lpc17_40_ssp0select()`
- `[lpc17_40_ssp.c:lpc17_40_ssp0status]` Public function `lpc17_40_ssp0status()`
- `[lpc17_40_ssp.c:lpc17_40_ssp1select]` Public function `lpc17_40_ssp1select()`
- `[lpc17_40_ssp.c:lpc17_40_ssp1status]` Public function `lpc17_40_ssp1status()`
- `[lpc17_40_ssp.c:lpc17_40_ssp0register]` Public function `lpc17_40_ssp0register()`
- `[lpc17_40_ssp.c:lpc17_40_ssp1register]` Public function `lpc17_40_ssp1register()`
- `[lpc17_40_usbmsc.c:board_usbmsc_initialize]` Public function `board_usbmsc_initialize()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_BUTTONS`, `CONFIG_CAN`, `CONFIG_USBMSC`
- `[lpc17_40_bringup.c:#error]` Compile-time guard: `CONFIG_LPC17_40_USBHOST is not selected`
- `[lpc17_40_can.c:lpc1766stk_can_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[lpc17_40_usbmsc.c:#error]` Compile-time guard: `Unrecognized LPC17xx/LPC40xx board`

## Side Effects
- `[lpc17_40_boot.c:lpc17_40_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `lpc1766stk_sspdev_initialize()`)
- `[lpc17_40_bringup.c:lpc17_40_bringup]` Configures or drives hardware GPIO pins
- `[lpc17_40_bringup.c:lpc17_40_bringup]` Initializes/registers kernel devices or filesystems (`lpc17_40_sspbus_initialize()`, `lpc17_40_usbhost_initialize()`, `nx_mount()`, `usbhost_cdcacm_initialize()`, `usbhost_hub_initialize()`)
- `[lpc17_40_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[lpc17_40_buttons.c:board_button_initialize]` Modifies interrupt controller or critical-section state
- `[lpc17_40_can.c:lpc1766stk_can_setup]` Initializes/registers kernel devices or filesystems (`can_register()`)
- `[lpc17_40_leds.c:board_userled]` Configures or drives hardware GPIO pins
- `[lpc17_40_leds.c:board_userled]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `board_userled_initialize()`, `led_initialize()`)
- `[lpc17_40_ssp.c:lpc1766stk_sspdev_initialize]` Configures or drives hardware GPIO pins
- `[lpc17_40_ssp.c:lpc1766stk_sspdev_initialize]` Modifies interrupt controller or critical-section state
- `[lpc17_40_usbmsc.c:board_usbmsc_initialize]` Configures or drives hardware GPIO pins
- `[lpc17_40_usbmsc.c:board_usbmsc_initialize]` Initializes/registers kernel devices or filesystems (`lpc17_40_sspbus_initialize()`)

## Verification
- Run: `./tools/configure.sh olimex-lpc1766stk:nsh && make`
