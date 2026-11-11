# `stm32h7s8-dk/src` Component (`boards/arm/stm32h7/stm32h7s8-dk/src`)

## Overview
Board-level C implementation (`src`) for `stm32h7s8-dk` (`arm/stm32h7`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[stm32h7s8-dk.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[stm32h7s8-dk.h:stm32_xspi_flash_initialize]` Public declaration `stm32_xspi_flash_initialize()`
- `[stm32h7s8-dk.h:stm32_xip_boot]` Public declaration `stm32_xip_boot()`
- `[stm32h7s8-dk.h:GPIO_LD1]` Hardware/board configuration macros (`GPIO_LD1`, `GPIO_LD2`, `GPIO_LD3`, `GPIO_LD4`, `GPIO_LED_GREEN`, `GPIO_LED_ORANGE` (+4 more))
- `[stm32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[stm32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_bringup.c:stm32_bringup]` Public function `stm32_bringup()`
- `[stm32_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[stm32_buttons.c:board_buttons]` Public function `board_buttons()`
- `[stm32_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[stm32_mx66uw1g45g.c:stm32_xspi_flash_initialize]` Public function `stm32_xspi_flash_initialize()`
- `[stm32_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[stm32_userleds.c:board_userled]` Public function `board_userled()`
- `[stm32_userleds.c:board_userled_all]` Public function `board_userled_all()`
- `[stm32_xip_boot.c:stm32_xip_boot]` Public function `stm32_xip_boot()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_STM32H7S8_DK_XIP_BOOTLOADER`
- `[stm32_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[stm32_mx66uw1g45g.c:stm32_xspi_flash_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_xip_boot.c:stm32_xip_boot]` Validates preconditions and returns `-EINVAL`, `-EIO` on failure

## Side Effects
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_boot.c:stm32_boardinitialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`btn_lower_initialize()`, `nx_mount()`, `userled_lower_initialize()`)
- `[stm32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[stm32_mx66uw1g45g.c:stm32_xspi_flash_initialize]` Initializes/registers kernel devices or filesystems (`mx66uw1g45g_initialize()`, `stm32_xspi_initialize()`)
- `[stm32_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_xip_boot.c:stm32_xip_boot]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[stm32_xip_boot.c:stm32_xip_boot]` Initializes/registers kernel devices or filesystems (`stm32_xspi_flash_initialize()`)

## Verification
- Run: `./tools/configure.sh stm32h7s8-dk:nsh && make`
