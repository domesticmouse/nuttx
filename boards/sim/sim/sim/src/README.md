# `sim/src` Component (`boards/sim/sim/sim/src`)

## Overview
Board-level C implementation (`src`) for `sim` (`sim/sim`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 10 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[sim.h:sim_bringup]` Public declaration `sim_bringup()`
- `[sim.h:sim_zoneinfo]` Public declaration `sim_zoneinfo()`
- `[sim.h:sim_gpio_initialize]` Public declaration `sim_gpio_initialize()`
- `[sim.h:sim_foc_setup]` Public declaration `sim_foc_setup()`
- `[sim.h:SIM_PROCFS_MOUNTPOINT]` Hardware/board configuration macros (`SIM_PROCFS_MOUNTPOINT`)
- `[dummy.c]` Translation unit `dummy.c`
- `[sim_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[sim_bringup.c:rpmsg_serialinit]` Public function `rpmsg_serialinit()`
- `[sim_bringup.c:sim_bringup]` Public function `sim_bringup()`
- `[sim_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[sim_buttons.c:board_buttons]` Public function `board_buttons()`
- `[sim_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[sim_buttons.c:up_buttonevent]` Public function `up_buttonevent()`
- `[sim_buttons.c:g_buttons]` Exported global symbol `g_buttons`
- `[sim_buttons.c:g_handler]` Exported global symbol `g_handler`
- `[sim_buttons.c:g_arg]` Exported global symbol `g_arg`
- `[sim_composite.c:board_composite_initialize]` Public function `board_composite_initialize()`
- `[sim_composite.c:board_composite_connect]` Public function `board_composite_connect()`
- `[sim_foc.c:sim_foc_setup]` Public function `sim_foc_setup()`
- `[sim_gpio.c:sim_gpio_initialize]` Public function `sim_gpio_initialize()`
- `[sim_ioexpander.c:sim_gpio_initialize]` Public function `sim_gpio_initialize()`
- `[sim_zoneinfo.c:sim_zoneinfo]` Public function `sim_zoneinfo()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_BUTTONS`, `CONFIG_BOARDCTL`, `CONFIG_BOARD_LATE_INITIALIZE`, `CONFIG_ETC_ROMFS`, `CONFIG_EXAMPLES_GPIO`, `CONFIG_GPIO_LOWER_HALF` (+4 more)
- `[sim_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[sim_foc.c:DEBUGASSERT]` Requires `foc[i]->lower`
- `[sim_gpio.c:DEBUGASSERT]` Requires `simgpint != NULL && simgpint->callback != NULL`
- `[sim_gpio.c:DEBUGASSERT]` Requires `simgpio != NULL && value != NULL`
- `[sim_gpio.c:DEBUGASSERT]` Requires `simgpio != NULL`
- `[sim_ioexpander.c:sim_gpio_initialize]` Validates preconditions and returns `-ENOMEM` on failure
- `[sim_zoneinfo.c:#error]` Compile-time guard: `CONFIG_LIBC_TZDIR is not defined`
- `[sim_zoneinfo.c:#error]` Compile-time guard: `Mountpoint support is disabled`

## Side Effects
- `[sim_bringup.c:rpmsg_serialinit]` Initializes/registers kernel devices or filesystems (`board_lcd_initialize()`, `btn_lower_initialize()`, `btnull_register()`, `fb_register()`, `i2c_register()`)
- `[sim_composite.c:board_composite_initialize]` Initializes/registers kernel devices or filesystems (`composite_initialize()`)
- `[sim_foc.c:sim_foc_setup]` Initializes/registers kernel devices or filesystems (`foc_dummy_initialize()`, `foc_register()`)
- `[sim_gpio.c:sim_gpio_initialize]` Initializes/registers kernel devices or filesystems (`gpio_pin_register()`)
- `[sim_ioexpander.c:sim_gpio_initialize]` Initializes/registers kernel devices or filesystems (`ioe_dummy_initialize()`)
- `[sim_zoneinfo.c:sim_zoneinfo]` Initializes/registers kernel devices or filesystems (`nx_mount()`, `romdisk_register()`)

## Verification
- Run: `./tools/configure.sh sim:nsh && make`
