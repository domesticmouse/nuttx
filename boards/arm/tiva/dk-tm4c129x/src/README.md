# `dk-tm4c129x/src` Component (`boards/arm/tiva/dk-tm4c129x/src`)

## Overview
Board-level C implementation (`src`) for `dk-tm4c129x` (`arm/tiva`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 10 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[dk-tm4c129x.h:tm4c_ssidev_initialize]` Public declaration `tm4c_ssidev_initialize()`
- `[dk-tm4c129x.h:tm4c_led_initialize]` Public declaration `tm4c_led_initialize()`
- `[dk-tm4c129x.h:tm4c_bringup]` Public declaration `tm4c_bringup()`
- `[dk-tm4c129x.h:tiva_timer_configure]` Public declaration `tiva_timer_configure()`
- `[dk-tm4c129x.h:HAVE_I2CTOOL]` Hardware/board configuration macros (`HAVE_I2CTOOL`, `GPIO_LED_R`, `GPIO_LED_G`, `GPIO_LED_B`, `GPIO_SW2`, `GPIO_SW3` (+7 more))
- `[tm4c_autoleds.c:tm4c_led_initialize]` Public function `tm4c_led_initialize()`
- `[tm4c_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[tm4c_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[tm4c_boot.c:tiva_boardinitialize]` Public function `tiva_boardinitialize()`
- `[tm4c_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[tm4c_bringup.c:tm4c_bringup]` Public function `tm4c_bringup()`
- `[tm4c_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[tm4c_buttons.c:board_buttons]` Public function `board_buttons()`
- `[tm4c_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[tm4c_ethernet.c:tiva_ethernetmac]` Public function `tiva_ethernetmac()`
- `[tm4c_ssi.c:tm4c_ssidev_initialize]` Public function `tm4c_ssidev_initialize()`
- `[tm4c_ssi.c:tiva_ssiselect]` Public function `tiva_ssiselect()`
- `[tm4c_ssi.c:tiva_ssistatus]` Public function `tiva_ssistatus()`
- `[tm4c_timer.c:tiva_timer_configure]` Public function `tiva_timer_configure()`
- `[tm4c_tmp100.c:tiva_tmp100_initialize]` Public function `tiva_tmp100_initialize()`
- `[tm4c_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[tm4c_userleds.c:board_userled]` Public function `board_userled()`
- `[tm4c_userleds.c:board_userled_all]` Public function `board_userled_all()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_DK_TM4C129X_TIMER`, `CONFIG_LM75_I2C`, `CONFIG_TIVA_ETHERNET`, `CONFIG_TIVA_I2C6`
- `[tm4c_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[tm4c_ethernet.c:DEBUGASSERT]` Requires `user0 != 0xffffffff && user1 != 0xffffffff`
- `[tm4c_timer.c:#error]` Compile-time guard: `CONFIG_TIMER is not defined`
- `[tm4c_timer.c:#error]` Compile-time guard: `CONFIG_TIVA_TIMER32_PERIODIC is not defined`
- `[tm4c_tmp100.c:tiva_tmp100_initialize]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[tm4c_autoleds.c:tm4c_led_initialize]` Configures or drives hardware GPIO pins
- `[tm4c_boot.c:tiva_boardinitialize]` Initializes/registers kernel devices or filesystems (`tm4c_led_initialize()`, `tm4c_ssidev_initialize()`)
- `[tm4c_bringup.c:tm4c_bringup]` Initializes/registers kernel devices or filesystems (`i2c_register()`, `tiva_i2cbus_initialize()`, `tiva_tmp100_initialize()`, `tm4c_i2c_register()`)
- `[tm4c_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[tm4c_buttons.c:board_button_initialize]` Modifies interrupt controller or critical-section state
- `[tm4c_timer.c:tiva_timer_configure]` Initializes/registers kernel devices or filesystems (`tiva_timer_register()`)
- `[tm4c_tmp100.c:tiva_tmp100_initialize]` Initializes/registers kernel devices or filesystems (`lm75_register()`, `tiva_i2cbus_initialize()`)
- `[tm4c_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh dk-tm4c129x:nsh && make`
