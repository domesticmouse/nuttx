# `nucleo-wb55rg/src` Component (`boards/arm/stm32wb/nucleo-wb55rg/src`)

## Overview
Board-level C implementation (`src`) for `nucleo-wb55rg` (`arm/stm32wb`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 4 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[nucleo-wb55rg.h:HAVE_RTC_DRIVER]` Hardware/board configuration macros (`HAVE_RTC_DRIVER`, `GPIO_LED1`, `GPIO_LED2`, `GPIO_LED3`, `GPIO_LED_BLUE`, `GPIO_LED_GREEN` (+7 more))
- `[stm32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[stm32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_boot.c:stm32_board_initialize]` Public function `stm32_board_initialize()`
- `[stm32_boot.c:arm_netinitialize]` Public function `arm_netinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_boot.c:board_ioctl]` Public function `board_ioctl()`
- `[stm32_boot.c:board_uniqueid]` Public function `board_uniqueid()`
- `[stm32_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[stm32_userleds.c:board_userled]` Public function `board_userled()`
- `[stm32_userleds.c:board_userled_all]` Public function `board_userled_all()`
- `[stm32_userleds.c:stm32_led_pminitialize]` Public function `stm32_led_pminitialize()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_LEDS`
- `[stm32_boot.c:stm32_board_initialize]` Validates preconditions and returns `-EINVAL`, `-ENOTTY` on failure

## Side Effects
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_boot.c:stm32_board_initialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `rtc_initialize()`, `stm32_blehci_initialize()`, `stm32_common_initialize()`)
- `[stm32_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_userleds.c:board_userled_initialize]` Initializes/registers kernel devices or filesystems (`pm_register()`)

## Verification
- Run: `./tools/configure.sh nucleo-wb55rg:nsh && make`
