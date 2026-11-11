# `photon/src` Component (`boards/arm/stm32f2/photon/src`)

## Overview
Board-level C implementation (`src`) for `photon` (`arm/stm32f2`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 14 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[photon.h:stm32_bringup]` Public declaration `stm32_bringup()`
- `[photon.h:stm32_spidev_initialize]` Public declaration `stm32_spidev_initialize()`
- `[photon.h:photon_watchdog_initialize]` Public declaration `photon_watchdog_initialize()`
- `[photon.h:stm32_rgbled_setup]` Public declaration `stm32_rgbled_setup()`
- `[photon.h:photon_wlan_initialize]` Public declaration `photon_wlan_initialize()`
- `[photon.h:stm32_usbinitialize]` Public declaration `stm32_usbinitialize()`
- `[photon.h:GPIO_LED1]` Hardware/board configuration macros (`GPIO_LED1`, `MIN_IRQBUTTON`, `MAX_IRQBUTTON`, `NUM_IRQBUTTONS`, `GPIO_BUTTON1`, `SDIO_WLAN0_SLOTNO` (+4 more))
- `[dfu_signature.c:dfu_sign]` Module symbol `dfu_sign`
- `[stm32_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[stm32_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[stm32_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[stm32_boot.c:stm32_boardinitialize]` Public function `stm32_boardinitialize()`
- `[stm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[stm32_bringup.c:stm32_bringup]` Public function `stm32_bringup()`
- `[stm32_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[stm32_buttons.c:board_buttons]` Public function `board_buttons()`
- `[stm32_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[stm32_composite.c:board_composite_initialize]` Public function `board_composite_initialize()`
- `[stm32_composite.c:board_composite_connect]` Public function `board_composite_connect()`
- `[stm32_rgbled.c:stm32_rgbled_setup]` Public function `stm32_rgbled_setup()`
- `[stm32_spi.c:stm32_spidev_initialize]` Public function `stm32_spidev_initialize()`
- `[stm32_spi.c:stm32_spi1select]` Public function `stm32_spi1select()`
- `[stm32_spi.c:stm32_spi1status]` Public function `stm32_spi1status()`
- *(+20 additional symbols across 14 files)*

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_LEDS`, `CONFIG_INPUT_BUTTONS`, `CONFIG_PHOTON_DFU_BOOTLOADER`, `CONFIG_PHOTON_WDG`, `CONFIG_PHOTON_WLAN` (+3 more)
- `[stm32_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[stm32_rgbled.c:#error]` Compile-time guard: `HAVE_RGBLED is undefined`
- `[stm32_spi.c:stm32_spidev_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[stm32_wdt.c:#error]` Compile-time guard: `No watchdog configured`

## Side Effects
- `[stm32_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_boot.c:stm32_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `stm32_spidev_initialize()`)
- `[stm32_bringup.c:stm32_bringup]` Initializes/registers kernel devices or filesystems (`board_button_initialize()`, `board_composite_initialize()`, `board_userled_initialize()`, `btn_lower_initialize()`, `nx_mount()`)
- `[stm32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[stm32_composite.c:board_composite_initialize]` Initializes/registers kernel devices or filesystems (`composite_initialize()`)
- `[stm32_rgbled.c:stm32_rgbled_setup]` Initializes/registers kernel devices or filesystems (`rgbled_register()`)
- `[stm32_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins
- `[stm32_wlan.c:bcmf_board_reset]` Configures or drives hardware GPIO pins
- `[stm32_wlan.c:bcmf_board_reset]` Initializes/registers kernel devices or filesystems (`bcmf_sdio_initialize()`, `sdio_initialize()`)

## Verification
- Run: `./tools/configure.sh photon:nsh && make`
