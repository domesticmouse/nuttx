# `spresense/src` Component (`boards/arm/cxd56xx/spresense/src`)

## Overview
Board-level C implementation (`src`) for `spresense` (`arm/cxd56xx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 19 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[spresense.h:cxd56_bringup]` Public declaration `cxd56_bringup()`
- `[cxd56_alt1250_power.c:board_alt1250_poweron]` Public function `board_alt1250_poweron()`
- `[cxd56_alt1250_power.c:board_alt1250_poweroff]` Public function `board_alt1250_poweroff()`
- `[cxd56_alt1250_power.c:board_alt1250_powerstatus]` Public function `board_alt1250_powerstatus()`
- `[cxd56_alt1250_power.c:board_alt1250_powerkeep]` Public function `board_alt1250_powerkeep()`
- `[cxd56_automount.c:board_automount_initialize]` Public function `board_automount_initialize()`
- `[cxd56_automount.c:board_automount_event]` Public function `board_automount_event()`
- `[cxd56_boardinit.c:board_late_initialize]` Public function `board_late_initialize()`
- `[cxd56_bringup.c:cxd56_bringup]` Public function `cxd56_bringup()`
- `[cxd56_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[cxd56_buttons.c:board_buttons]` Public function `board_buttons()`
- `[cxd56_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[cxd56_charger.c:board_charger_initialize]` Public function `board_charger_initialize()`
- `[cxd56_charger.c:board_charger_uninitialize]` Public function `board_charger_uninitialize()`
- `[cxd56_clock.c:board_clock_initialize]` Public function `board_clock_initialize()`
- `[cxd56_clock.c:board_clock_enable]` Public function `board_clock_enable()`
- `[cxd56_composite.c:board_composite_initialize]` Public function `board_composite_initialize()`
- `[cxd56_composite.c:board_composite_connect]` Public function `board_composite_connect()`
- `[cxd56_gauge.c:board_gauge_initialize]` Public function `board_gauge_initialize()`
- `[cxd56_gauge.c:board_gauge_uninitialize]` Public function `board_gauge_uninitialize()`
- `[cxd56_gpioif.c:board_gpio_config]` Public function `board_gpio_config()`
- `[cxd56_gpioif.c:board_gpio_status]` Public function `board_gpio_status()`
- `[cxd56_gpioif.c:board_gpio_write]` Public function `board_gpio_write()`
- *(+49 additional symbols across 19 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_BOARDCTL_IOCTL`, `CONFIG_CXD56_CHARGER`, `CONFIG_CXD56_GAUGE` (+7 more)
- `[cxd56_automount.c:DEBUGASSERT]` Requires `config && config->state`
- `[cxd56_charger.c:board_charger_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[cxd56_composite.c:DEBUGASSERT]` Requires `g_mschandle == NULL`
- `[cxd56_composite.c:DEBUGASSERT]` Requires `g_mschandle != NULL`
- `[cxd56_composite.c:#error]` Compile-time guard: `Configuration not supported, not enough endpoints`
- `[cxd56_gauge.c:board_gauge_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[cxd56_gpioif.c:DEBUGASSERT]` Requires `input`
- `[cxd56_gpioif.c:DEBUGASSERT]` Requires `output`
- `[cxd56_gpioif.c:DEBUGASSERT]` Requires `drive`
- `[cxd56_ioctl.c:board_ioctl]` Validates preconditions and returns `-ENOTTY` on failure
- `[cxd56_pwm.c:board_pwm_setup]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[cxd56_alt1250_power.c:board_alt1250_poweron]` Configures or drives hardware GPIO pins
- `[cxd56_automount.c:board_automount_initialize]` Initializes/registers kernel devices or filesystems (`automount_initialize()`)
- `[cxd56_automount.c:board_automount_initialize]` Modifies interrupt controller or critical-section state
- `[cxd56_bringup.c:cxd56_bringup]` Configures or drives hardware GPIO pins
- `[cxd56_bringup.c:cxd56_bringup]` Initializes/registers kernel devices or filesystems (`board_alt1250_initialize()`, `board_automount_initialize()`, `board_clock_initialize()`, `board_cxd5602pwbimu_initialize()`, `board_emmc_initialize()`)
- `[cxd56_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[cxd56_charger.c:board_charger_initialize]` Initializes/registers kernel devices or filesystems (`cxd56_charger_initialize()`)
- `[cxd56_composite.c:board_composite_initialize]` Initializes/registers kernel devices or filesystems (`composite_initialize()`)
- `[cxd56_gauge.c:board_gauge_initialize]` Initializes/registers kernel devices or filesystems (`cxd56_gauge_initialize()`)
- `[cxd56_gpioif.c:board_gpio_config]` Configures or drives hardware GPIO pins
- `[cxd56_leds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[cxd56_power.c:board_pmic_read]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh spresense:nsh && make`
