# `emw3162/src` Component (`boards/arm/stm32f2/emw3162/src`)

## Overview
Board-level C implementation (`src`) for `emw3162` (`arm/stm32f2`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 6 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[emw3162.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[emw3162.h:emw3162_wlan_initialize]` Public declaration `emw3162_wlan_initialize()`
- `[emw3162.h:GPIO_LED1]` Hardware/board configuration macros (`GPIO_LED1`, `GPIO_LED2`, `SDIO_WLAN0_SLOTNO`, `SDIO_WLAN0_MINOR`, `GPIO_WLAN0_RESET`, `GPIO_WLAN0_PWRDN` (+1 more))
- `[stm32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[stm32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_bringup.c:stm32_bringup]` Public function `stm32_bringup()`
- `[stm32_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[stm32_userleds.c:board_userled]` Public function `board_userled()`
- `[stm32_userleds.c:board_userled_all]` Public function `board_userled_all()`
- `[stm32_wlan.c:bcmf_board_reset]` Public function `bcmf_board_reset()`
- `[stm32_wlan.c:bcmf_board_power]` Public function `bcmf_board_power()`
- `[stm32_wlan.c:bcmf_board_initialize]` Public function `bcmf_board_initialize()`
- `[stm32_wlan.c:bcmf_board_setup_oob_irq]` Public function `bcmf_board_setup_oob_irq()`
- `[stm32_wlan.c:bcmf_board_etheraddr]` Public function `bcmf_board_etheraddr()`
- `[stm32_wlan.c:emw3162_wlan_initialize]` Public function `emw3162_wlan_initialize()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_LEDS`, `CONFIG_EMW3162_WLAN`

## Side Effects
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`board_userled_initialize()`, `emw3162_wlan_initialize()`, `nx_mount()`, `userled_lower_initialize()`)
- `[stm32_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_wlan.c:bcmf_board_reset]` Configures or drives hardware GPIO pins
- `[stm32_wlan.c:bcmf_board_reset]` Initializes/registers kernel devices or filesystems (`bcmf_sdio_initialize()`, `sdio_initialize()`)

## Verification
- Run: `./tools/configure.sh emw3162:nsh && make`
