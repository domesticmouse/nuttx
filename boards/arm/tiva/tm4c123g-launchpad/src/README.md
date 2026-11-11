# `tm4c123g-launchpad/src` Component (`boards/arm/tiva/tm4c123g-launchpad/src`)

## Overview
Board-level C implementation (`src`) for `tm4c123g-launchpad` (`arm/tiva`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 11 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[tm4c123g-launchpad.h:tm4c_ssidev_initialize]` Public declaration `tm4c_ssidev_initialize()`
- `[tm4c123g-launchpad.h:tm4c_led_initialize]` Public declaration `tm4c_led_initialize()`
- `[tm4c123g-launchpad.h:tm4c_bringup]` Public declaration `tm4c_bringup()`
- `[tm4c123g-launchpad.h:tm4c_adc_setup]` Public declaration `tm4c_adc_setup()`
- `[tm4c123g-launchpad.h:tm4c_can_setup]` Public declaration `tm4c_can_setup()`
- `[tm4c123g-launchpad.h:tm4c_at24_automount]` Public declaration `tm4c_at24_automount()`
- `[tm4c123g-launchpad.h:tiva_timer_configure]` Public declaration `tiva_timer_configure()`
- `[tm4c123g-launchpad.h:tiva_mcp2515initialize]` Public declaration `tiva_mcp2515initialize()`
- `[tm4c123g-launchpad.h:HAVE_AT24]` Hardware/board configuration macros (`HAVE_AT24`, `AT24_BUS`, `AT24_MINOR`, `GPIO_LED_R`, `GPIO_LED_G`, `GPIO_LED_B` (+8 more))
- `[tm4c_adc.c:tm4c_adc_setup]` Public function `tm4c_adc_setup()`
- `[tm4c_adc.c:adc_timer_init]` Public function `adc_timer_init()`
- `[tm4c_at24.c:tm4c_at24_automount]` Public function `tm4c_at24_automount()`
- `[tm4c_autoleds.c:tm4c_led_initialize]` Public function `tm4c_led_initialize()`
- `[tm4c_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[tm4c_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[tm4c_boot.c:tiva_boardinitialize]` Public function `tiva_boardinitialize()`
- `[tm4c_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[tm4c_bringup.c:tm4c_bringup]` Public function `tm4c_bringup()`
- `[tm4c_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[tm4c_buttons.c:board_buttons]` Public function `board_buttons()`
- `[tm4c_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[tm4c_can.c:tm4c_can_setup]` Public function `tm4c_can_setup()`
- `[tm4c_mcp2515.c:mcp2515_interrupt]` Public function `mcp2515_interrupt()`
- *(+5 additional symbols across 11 files)*

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_CAN_MCP2515`, `CONFIG_MTD_AT24XX`, `CONFIG_TIVA_ADC`, `CONFIG_TIVA_CAN` (+2 more)
- `[tm4c_at24.c:tm4c_at24_automount]` Validates preconditions and returns `-ENODEV` on failure
- `[tm4c_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[tm4c_mcp2515.c:DEBUGASSERT]` Requires `priv != NULL`
- `[tm4c_timer.c:#error]` Compile-time guard: `CONFIG_TIVA_TIMER32_PERIODIC is not defined`

## Side Effects
- `[tm4c_adc.c:tm4c_adc_setup]` Initializes/registers kernel devices or filesystems (`tiva_adc_initialize()`)
- `[tm4c_at24.c:tm4c_at24_automount]` Initializes/registers kernel devices or filesystems (`at24c_initialize()`, `nx_mount()`, `nxffs_initialize()`, `tiva_i2cbus_initialize()`)
- `[tm4c_autoleds.c:tm4c_led_initialize]` Configures or drives hardware GPIO pins
- `[tm4c_boot.c:tiva_boardinitialize]` Initializes/registers kernel devices or filesystems (`tm4c_led_initialize()`, `tm4c_ssidev_initialize()`)
- `[tm4c_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[tm4c_can.c:tm4c_can_setup]` Configures or drives hardware GPIO pins
- `[tm4c_can.c:tm4c_can_setup]` Initializes/registers kernel devices or filesystems (`tiva_can_initialize()`)
- `[tm4c_mcp2515.c:mcp2515_interrupt]` Configures or drives hardware GPIO pins
- `[tm4c_mcp2515.c:mcp2515_interrupt]` Initializes/registers kernel devices or filesystems (`can_register()`, `mcp2515_initialize()`, `tiva_ssibus_initialize()`)
- `[tm4c_mcp2515.c:mcp2515_interrupt]` Modifies interrupt controller or critical-section state
- `[tm4c_ssi.c:tm4c_ssidev_initialize]` Configures or drives hardware GPIO pins
- `[tm4c_timer.c:tiva_timer_configure]` Initializes/registers kernel devices or filesystems (`tiva_timer_initialize()`)

## Verification
- Run: `./tools/configure.sh tm4c123g-launchpad:nsh && make`
