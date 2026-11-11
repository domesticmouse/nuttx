# `metro-m4/src` Component (`boards/arm/samd5e5/metro-m4/src`)

## Overview
Board-level C implementation (`src`) for `metro-m4` (`arm/samd5e5`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 15 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[metro-m4.h:sam_bringup]` Public declaration `sam_bringup()`
- `[metro-m4.h:sam_led_pminitialize]` Public declaration `sam_led_pminitialize()`
- `[metro-m4.h:sam_automount_initialize]` Public declaration `sam_automount_initialize()`
- `[metro-m4.h:sam_automount_event]` Public declaration `sam_automount_event()`
- `[metro-m4.h:metro_m4_i2cdev_initialize]` Public declaration `metro_m4_i2cdev_initialize()`
- `[metro-m4.h:sam_smartfs_initialize]` Public declaration `sam_smartfs_initialize()`
- `[metro-m4.h:sam_bq27426_initialize]` Public declaration `sam_bq27426_initialize()`
- `[metro-m4.h:sam_gpio_initialize]` Public declaration `sam_gpio_initialize()`
- `[metro-m4.h:PORT_RED_LED]` Hardware/board configuration macros (`PORT_RED_LED`, `PORT_D8`, `PORT_D9`, `PORT_D10`, `BOARD_NGPIOIN`, `BOARD_NGPIOOUT` (+6 more))
- `[sam_at24.c:sam_at24_automount]` Public function `sam_at24_automount()`
- `[sam_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[sam_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[sam_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[sam_autoleds.c:sam_led_pminitialize]` Public function `sam_led_pminitialize()`
- `[sam_automount.c:sam_automount_initialize]` Public function `sam_automount_initialize()`
- `[sam_automount.c:sam_automount_event]` Public function `sam_automount_event()`
- `[sam_boot.c:sam_board_initialize]` Public function `sam_board_initialize()`
- `[sam_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[sam_bq27426.c:sam_bq27426_initialize]` Public function `sam_bq27426_initialize()`
- `[sam_bringup.c:sam_bringup]` Public function `sam_bringup()`
- `[sam_composite.c:board_composite_initialize]` Public function `board_composite_initialize()`
- `[sam_composite.c:board_composite_connect]` Public function `board_composite_connect()`
- `[sam_gpio.c:sam_gpio_initialize]` Public function `sam_gpio_initialize()`
- *(+13 additional symbols across 15 files)*

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_LEDS`, `CONFIG_BQ27426`, `CONFIG_DEV_GPIO`, `CONFIG_FS_AUTOMOUNTER`, `CONFIG_FS_SMARTFS`, `CONFIG_MTD_AT24XX` (+5 more)
- `[sam_at24.c:sam_at24_automount]` Validates preconditions and returns `-ENODEV` on failure
- `[sam_automount.c:DEBUGASSERT]` Requires `config && config->state`
- `[sam_composite.c:DEBUGASSERT]` Requires `g_mschandle == NULL`
- `[sam_composite.c:DEBUGASSERT]` Requires `g_mschandle != NULL`
- `[sam_gpio.c:DEBUGASSERT]` Requires `samgpint != NULL && samgpint->callback != NULL`
- `[sam_gpio.c:DEBUGASSERT]` Requires `samgpio != NULL && value != NULL`
- `[sam_gpio.c:DEBUGASSERT]` Requires `samgpio->id < BOARD_NGPIOIN`
- `[sam_i2c.c:metro_m4_i2cdev_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[sam_usbhost.c:DEBUGASSERT]` Requires `iface == 0`

## Side Effects
- `[sam_at24.c:sam_at24_automount]` Initializes/registers kernel devices or filesystems (`at24c_initialize()`, `nx_mount()`, `nxffs_initialize()`)
- `[sam_autoleds.c:board_autoled_initialize]` Initializes/registers kernel devices or filesystems (`pm_register()`)
- `[sam_automount.c:sam_automount_initialize]` Initializes/registers kernel devices or filesystems (`automount_initialize()`)
- `[sam_automount.c:sam_automount_initialize]` Modifies interrupt controller or critical-section state
- `[sam_boot.c:sam_board_initialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[sam_bq27426.c:sam_bq27426_initialize]` Initializes/registers kernel devices or filesystems (`battery_gauge_register()`, `bq27426_initialize()`)
- `[sam_bringup.c:sam_bringup]` Initializes/registers kernel devices or filesystems (`metro_m4_i2cdev_initialize()`, `nx_mount()`, `sam_automount_initialize()`, `sam_bq27426_initialize()`, `sam_gpio_initialize()`)
- `[sam_composite.c:board_composite_initialize]` Initializes/registers kernel devices or filesystems (`composite_initialize()`)
- `[sam_gpio.c:sam_gpio_initialize]` Initializes/registers kernel devices or filesystems (`gpio_pin_register()`)
- `[sam_gpio.c:sam_gpio_initialize]` Modifies interrupt controller or critical-section state
- `[sam_i2c.c:metro_m4_i2cdev_initialize]` Initializes/registers kernel devices or filesystems (`i2c_register()`, `sam_i2c_master_initialize()`)
- `[sam_smartfs.c:sam_smartfs_initialize]` Initializes/registers kernel devices or filesystems (`mtdconfig_register()`, `progmem_initialize()`, `sam_progmem_initialize()`, `smart_initialize()`)

## Verification
- Run: `./tools/configure.sh metro-m4:nsh && make`
