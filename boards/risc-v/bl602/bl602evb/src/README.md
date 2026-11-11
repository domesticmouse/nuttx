# `bl602evb/src` Component (`boards/risc-v/bl602/bl602evb/src`)

## Overview
Board-level C implementation (`src`) for `bl602evb` (`risc-v/bl602`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 6 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[bl602evb.h:bl602_bringup]` Public declaration `bl602_bringup()`
- `[bl602_boardctl.c:board_ioctl]` Public function `board_ioctl()`
- `[bl602_boardctl.c:board_uniqueid]` Public function `board_uniqueid()`
- `[bl602_boot.c:bl602_boardinitialize]` Public function `bl602_boardinitialize()`
- `[bl602_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[bl602_bringup.c:bl602_net_initialize]` Public function `bl602_net_initialize()`
- `[bl602_bringup.c:rw_main_task_post_from_fw]` Public function `rw_main_task_post_from_fw()`
- `[bl602_bringup.c:bl602_hci_uart_api_init]` Public function `bl602_hci_uart_api_init()`
- `[bl602_bringup.c:bthci_register]` Public function `bthci_register()`
- `[bl602_bringup.c:bl602_hci_uart_init]` Public function `bl602_hci_uart_init()`
- `[bl602_bringup.c:bl602_bringup]` Public function `bl602_bringup()`
- `[bl602_gpio.c:bl602_gpio_initialize]` Public function `bl602_gpio_initialize()`
- `[bl602_reset.c:board_reset]` Public function `board_reset()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_BOARDCTL`, `CONFIG_BOARDCTL_RESET`, `CONFIG_DEV_GPIO`
- `[bl602_boardctl.c:DEBUGASSERT]` Requires `CONFIG_BOARDCTL_UNIQUEID_SIZE >= 6`
- `[bl602_bringup.c:bl602_net_initialize]` Validates preconditions and returns `-EINVAL`, `-ENOMEM` on failure
- `[bl602_gpio.c:DEBUGASSERT]` Requires `bl602xgpint != NULL && bl602xgpint->callback != NULL`
- `[bl602_gpio.c:DEBUGASSERT]` Requires `bl602xgpint != NULL`
- `[bl602_gpio.c:DEBUGASSERT]` Requires `bl602xgpio != NULL && value != NULL`
- `[bl602_reset.c:board_reset]` Validates preconditions and returns `-EINVAL`, `-EIO` on failure

## Side Effects
- `[bl602_bringup.c:bl602_net_initialize]` Initializes/registers kernel devices or filesystems (`bl602_gpio_initialize()`, `bl602_i2cbus_initialize()`, `bl602_rtc_lowerhalf_initialize()`, `bl602_spibus_initialize()`, `bl602_timer_initialize()`)
- `[bl602_bringup.c:bl602_net_initialize]` Modifies interrupt controller or critical-section state
- `[bl602_gpio.c:bl602_gpio_initialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[bl602_gpio.c:bl602_gpio_initialize]` Configures or drives hardware GPIO pins
- `[bl602_gpio.c:bl602_gpio_initialize]` Initializes/registers kernel devices or filesystems (`gpio_pin_register()`)
- `[bl602_gpio.c:bl602_gpio_initialize]` Modifies interrupt controller or critical-section state

## Verification
- Run: `./tools/configure.sh bl602evb:nsh && make`
