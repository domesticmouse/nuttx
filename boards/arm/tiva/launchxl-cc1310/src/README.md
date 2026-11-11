# `launchxl-cc1310/src` Component (`boards/arm/tiva/launchxl-cc1310/src`)

## Overview
Board-level C implementation (`src`) for `launchxl-cc1310` (`arm/tiva`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[launchxl-cc1310.h:cc1310_bringup]` Public declaration `cc1310_bringup()`
- `[launchxl-cc1310.h:cc1310_ssidev_initialize]` Public declaration `cc1310_ssidev_initialize()`
- `[launchxl-cc1310.h:CC1310_SW1_IRQ]` Hardware/board configuration macros (`CC1310_SW1_IRQ`, `CC1310_SW2_IRQ`)
- `[cc1310_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[cc1310_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[cc1310_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[cc1310_boot.c:tiva_boardinitialize]` Public function `tiva_boardinitialize()`
- `[cc1310_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[cc1310_bringup.c:cc1310_bringup]` Public function `cc1310_bringup()`
- `[cc1310_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[cc1310_buttons.c:board_buttons]` Public function `board_buttons()`
- `[cc1310_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[cc1310_pinconfig.c:g_gpio_uart0_rx]` Exported global symbol `g_gpio_uart0_rx`
- `[cc1310_pinconfig.c:g_gpio_uart0_tx]` Exported global symbol `g_gpio_uart0_tx`
- `[cc1310_pinconfig.c:g_gpio_gled]` Exported global symbol `g_gpio_gled`
- `[cc1310_pinconfig.c:g_gpio_rled]` Exported global symbol `g_gpio_rled`
- `[cc1310_pinconfig.c:g_gpio_sw1]` Exported global symbol `g_gpio_sw1`
- `[cc1310_pinconfig.c:g_gpio_sw2]` Exported global symbol `g_gpio_sw2`
- `[cc1310_ssi.c:cc1310_ssidev_initialize]` Public function `cc1310_ssidev_initialize()`
- `[cc1310_ssi.c:tiva_ssiselect]` Public function `tiva_ssiselect()`
- `[cc1310_ssi.c:tiva_ssistatus]` Public function `tiva_ssistatus()`
- `[cc1310_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[cc1310_userleds.c:board_userled]` Public function `board_userled()`
- `[cc1310_userleds.c:board_userled_all]` Public function `board_userled_all()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_TIVA_SSI`
- `[cc1310_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure

## Side Effects
- `[cc1310_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[cc1310_boot.c:tiva_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `cc1310_ssidev_initialize()`)
- `[cc1310_bringup.c:cc1310_bringup]` Initializes/registers kernel devices or filesystems (`nx_mount()`)
- `[cc1310_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[cc1310_buttons.c:board_button_initialize]` Modifies interrupt controller or critical-section state
- `[cc1310_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh launchxl-cc1310:nsh && make`
