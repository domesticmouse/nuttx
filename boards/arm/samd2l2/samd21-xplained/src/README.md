# `samd21-xplained/src` Component (`boards/arm/samd2l2/samd21-xplained/src`)

## Overview
Board-level C implementation (`src`) for `samd21-xplained` (`arm/samd2l2`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 8 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[samd21-xplained.h:sam_spidev_initialize]` Public declaration `sam_spidev_initialize()`
- `[samd21-xplained.h:sam_sdinitialize]` Public declaration `sam_sdinitialize()`
- `[samd21-xplained.h:PORT_STATUS_LED]` Hardware/board configuration macros (`PORT_STATUS_LED`, `PORT_SW0`, `IRQ_SW0`, `PORT_SD_CD`, `PORT_SD_CS`, `PORT_OLED_DATA` (+2 more))
- `[sam_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[sam_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[sam_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[sam_boot.c:sam_boardinitialize]` Public function `sam_boardinitialize()`
- `[sam_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[sam_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[sam_buttons.c:board_buttons]` Public function `board_buttons()`
- `[sam_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[sam_mmcsd.c:sam_sdinitialize]` Public function `sam_sdinitialize()`
- `[sam_spi.c:sam_spidev_initialize]` Public function `sam_spidev_initialize()`
- `[sam_spi.c:sam_spi0select]` Public function `sam_spi0select()`
- `[sam_spi.c:sam_spi1select]` Public function `sam_spi1select()`
- `[sam_spi.c:sam_spi2select]` Public function `sam_spi2select()`
- `[sam_spi.c:sam_spi3select]` Public function `sam_spi3select()`
- `[sam_spi.c:sam_spi4select]` Public function `sam_spi4select()`
- `[sam_spi.c:sam_spi5select]` Public function `sam_spi5select()`
- `[sam_spi.c:sam_spi0status]` Public function `sam_spi0status()`
- `[sam_spi.c:sam_spi1status]` Public function `sam_spi1status()`
- `[sam_spi.c:sam_spi2status]` Public function `sam_spi2status()`
- `[sam_spi.c:sam_spi3status]` Public function `sam_spi3status()`
- *(+12 additional symbols across 8 files)*

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_LCD_UG2832HSWEG04`, `CONFIG_SAMD21_XPLAINED_IOMODULE`, `CONFIG_SAMD21_XPLAINED_OLED1MODULE`, `CONFIG_SAMD2L2_SERCOM0`
- `[samd21-xplained.h:#error]` Compile-time guard: `SAMD2L2_HAVE_SPI0 is required to use the I/O1 module`
- `[samd21-xplained.h:#error]` Compile-time guard: `I/O1 and OLED1 modules cannot both reside in EXT1`
- `[sam_boot.c:#error]` Compile-time guard: `I/O1 module on EXT1 requires SERCOM SPI0`
- `[sam_boot.c:#error]` Compile-time guard: `I/O1 module on EXT2 requires SERCOM SPI1`
- `[sam_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[sam_mmcsd.c:#error]` Compile-time guard: `Mountpoints are disabled (CONFIG_DISABLE_MOUNTPOINT=y)`
- `[sam_mmcsd.c:#error]` Compile-time guard: `SERCOM0 SPI support is required`
- `[sam_ug2832hsweg04.c:#error]` Compile-time guard: `The OLED driver requires CONFIG_LCD_SSD1306 in the configuration`
- `[sam_ug2832hsweg04.c:#error]` Compile-time guard: `The OLED driver requires CONFIG_LCD_UG2832HSWEG04 in the configuration`

## Side Effects
- `[sam_boot.c:sam_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `sam_spidev_initialize()`)
- `[sam_buttons.c:board_button_initialize]` Modifies interrupt controller or critical-section state
- `[sam_mmcsd.c:sam_sdinitialize]` Initializes/registers kernel devices or filesystems (`sam_spibus_initialize()`)
- `[sam_ug2832hsweg04.c:board_graphics_setup]` Initializes/registers kernel devices or filesystems (`sam_spibus_initialize()`, `ssd1306_initialize()`)

## Verification
- Run: `./tools/configure.sh samd21-xplained:nsh && make`
