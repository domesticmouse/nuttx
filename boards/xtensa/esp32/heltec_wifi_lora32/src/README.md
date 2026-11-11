# `heltec_wifi_lora32/src` Component (`boards/xtensa/esp32/heltec_wifi_lora32/src`)

## Overview
Board-level C implementation (`src`) for `heltec_wifi_lora32` (`xtensa/esp32`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[heltec_wifi_lora32.h:esp32_bringup]` Public declaration `esp32_bringup()`
- `[heltec_wifi_lora32.h:esp32_lpwaninitialize]` Public declaration `esp32_lpwaninitialize()`
- `[heltec_wifi_lora32.h:GPIO_SX127X_RESET]` Hardware/board configuration macros (`GPIO_SX127X_RESET`, `GPIO_SX127X_DIO0`, `BUTTON_BOOT`, `PCNT_QE0_ID`, `GPIO_MCP2515_IRQ`, `TIMER0` (+9 more))
- `[esp32_boot.c:esp32_board_initialize]` Public function `esp32_board_initialize()`
- `[esp32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[esp32_bringup.c:esp32_bringup]` Public function `esp32_bringup()`
- `[esp32_sx127x.c:esp32_lpwaninitialize]` Public function `esp32_lpwaninitialize()`
- `[esp32_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[esp32_userleds.c:board_userled]` Public function `board_userled()`
- `[esp32_userleds.c:board_userled_all]` Public function `board_userled_all()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_LPWAN_SX127X`, `CONFIG_USERLED`
- `[esp32_sx127x.c:esp32_lpwaninitialize]` Validates preconditions and returns `-EINVAL`, `-ENODEV` on failure

## Side Effects
- `[esp32_bringup.c:esp32_bringup]` Initializes/registers kernel devices or filesystems (`nx_mount()`, `userled_lower_initialize()`)
- `[esp32_sx127x.c:esp32_lpwaninitialize]` Configures or drives hardware GPIO pins
- `[esp32_sx127x.c:esp32_lpwaninitialize]` Initializes/registers kernel devices or filesystems (`esp32_spibus_initialize()`, `sx127x_register()`)
- `[esp32_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh heltec_wifi_lora32:nsh && make`
