# `arduino-due/src` Component (`boards/arm/sam34/arduino-due/src`)

## Overview
Board-level C implementation (`src`) for `arduino-due` (`arm/sam34`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[arduino-due.h:sam_bringup]` Public declaration `sam_bringup()`
- `[arduino-due.h:sam_sdinitialize]` Public declaration `sam_sdinitialize()`
- `[arduino-due.h:sam_tsc_setup]` Public declaration `sam_tsc_setup()`
- `[arduino-due.h:GPIO_LED_L]` Hardware/board configuration macros (`GPIO_LED_L`, `GPIO_LED_RX`, `GPIO_LED_TX`, `GPIO_SD_SCK`, `GPIO_SD_MISO`, `GPIO_SD_MOSI` (+17 more))
- `[sam_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[sam_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[sam_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[sam_boot.c:sam_boardinitialize]` Public function `sam_boardinitialize()`
- `[sam_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[sam_bringup.c:sam_bringup]` Public function `sam_bringup()`
- `[sam_mmcsd.c:sam_sdinitialize]` Public function `sam_sdinitialize()`
- `[sam_spidev.c:sam_spi0select]` Public function `sam_spi0select()`
- `[sam_spidev.c:sam_spi0status]` Public function `sam_spi0status()`
- `[sam_touchscreen.c:sam_tsc_setup]` Public function `sam_tsc_setup()`
- `[sam_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[sam_userleds.c:board_userled]` Public function `board_userled()`
- `[sam_userleds.c:board_userled_all]` Public function `board_userled_all()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_LEDS`, `CONFIG_ARDUINO_ITHEAD_TFT`, `CONFIG_INPUT_ADS7843E`, `CONFIG_LCD`, `CONFIG_MMCSD_SPI`, `CONFIG_SAM34_SPI0` (+1 more)
- `[arduino-due.h:#error]` Compile-time guard: `LEDs may not be used with the ITEAD SD card`
- `[arduino-due.h:#error]` Compile-time guard: `UART0 cannot be used with the ITEAD LCD`
- `[sam_bringup.c:#error]` Compile-time guard: `Only one MMC/SD slot: Slot 0 (CONFIG_NSH_MMCSDSLOTNO)`
- `[sam_mmcsd.c:#error]` Compile-time guard: `Mountpoints are disabled (CONFIG_DISABLE_MOUNTPOINT=y)`
- `[sam_touchscreen.c:DEBUGASSERT]` Requires `minor == 0`
- `[sam_touchscreen.c:#error]` Compile-time guard: `Touchscreen support requires CONFIG_SAM34_GPIOC_IRQ`

## Side Effects
- `[sam_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[sam_boot.c:sam_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[sam_bringup.c:sam_bringup]` Configures or drives hardware GPIO pins
- `[sam_bringup.c:sam_bringup]` Initializes/registers kernel devices or filesystems (`board_userled_initialize()`, `nx_mount()`, `sam_spibus_initialize()`, `spi_register()`, `userled_lower_initialize()`)
- `[sam_mmcsd.c:sam_sdinitialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[sam_mmcsd.c:sam_sdinitialize]` Configures or drives hardware GPIO pins
- `[sam_spidev.c:sam_spi0select]` Configures or drives hardware GPIO pins
- `[sam_touchscreen.c:sam_tsc_setup]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[sam_touchscreen.c:sam_tsc_setup]` Configures or drives hardware GPIO pins
- `[sam_touchscreen.c:sam_tsc_setup]` Initializes/registers kernel devices or filesystems (`ads7843e_register()`)
- `[sam_touchscreen.c:sam_tsc_setup]` Modifies interrupt controller or critical-section state
- `[sam_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh arduino-due:nsh && make`
