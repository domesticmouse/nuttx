# `sam4l-xplained/src` Component (`boards/arm/sam34/sam4l-xplained/src`)

## Overview
Board-level C implementation (`src`) for `sam4l-xplained` (`arm/sam34`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 9 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[sam4l-xplained.h:sam_spidev_initialize]` Public declaration `sam_spidev_initialize()`
- `[sam4l-xplained.h:sam_sdinitialize]` Public declaration `sam_sdinitialize()`
- `[sam4l-xplained.h:sam_slcd_initialize]` Public declaration `sam_slcd_initialize()`
- `[sam4l-xplained.h:GPIO_LED0]` Hardware/board configuration macros (`GPIO_LED0`, `GPIO_SW0`, `IRQ_SW0`, `GPIO_LCD1_BL`, `GPIO_SD_CD`, `IRQ_SD_CD` (+8 more))
- `[sam_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[sam_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[sam_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[sam_boot.c:sam_boardinitialize]` Public function `sam_boardinitialize()`
- `[sam_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[sam_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[sam_buttons.c:board_buttons]` Public function `board_buttons()`
- `[sam_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[sam_mmcsd.c:sam_sdinitialize]` Public function `sam_sdinitialize()`
- `[sam_slcd.c:sam_slcd_initialize]` Public function `sam_slcd_initialize()`
- `[sam_spi.c:sam_spidev_initialize]` Public function `sam_spidev_initialize()`
- `[sam_spi.c:sam_spi0select]` Public function `sam_spi0select()`
- `[sam_spi.c:sam_spi0status]` Public function `sam_spi0status()`
- `[sam_spi.c:sam_spic0mddata]` Public function `sam_spic0mddata()`
- `[sam_ug2832hsweg04.c:board_graphics_setup]` Public function `board_graphics_setup()`
- `[sam_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[sam_userleds.c:board_userled]` Public function `board_userled()`
- `[sam_userleds.c:board_userled_all]` Public function `board_userled_all()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_LCD_UG2832HSWEG04`, `CONFIG_SAM34_LCDCA`, `CONFIG_SAM34_SPI0`, `CONFIG_SAM4L_XPLAINED_IOMODULE` (+2 more)
- `[sam4l-xplained.h:#error]` Compile-time guard: `CONFIG_SAM34_LCDCA is required to use the LCD1 module`
- `[sam4l-xplained.h:#error]` Compile-time guard: `CONFIG_SAM34_SPI0 is required to use the I/O1 module`
- `[sam_boot.c:#error]` Compile-time guard: `Only one MMC/SD slot: Slot 0 (CONFIG_NSH_MMCSDSLOTNO)`
- `[sam_boot.c:#error]` Compile-time guard: `CONFIG_NSH_MMCSDSPIPORTNO must have the same value as SD_CSNO`
- `[sam_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[sam_mmcsd.c:#error]` Compile-time guard: `Mountpoints are disabled (CONFIG_DISABLE_MOUNTPOINT=y)`
- `[sam_mmcsd.c:#error]` Compile-time guard: `SPI support is required (CONFIG_SAM34_SPI0)`
- `[sam_slcd.c:#error]` Compile-time guard: `This SLCD driver requires CONFIG_LIBC_SLCDCODEC`
- `[sam_slcd.c:#error]` Compile-time guard: `This SLCD driver requires that either CONFIG_SAM34_OSC32K or`
- `[sam_ug2832hsweg04.c:#error]` Compile-time guard: `The OLED driver requires CONFIG_LCD_SSD1306 in the configuration`
- `[sam_ug2832hsweg04.c:#error]` Compile-time guard: `The OLED driver requires CONFIG_LCD_UG2832HSWEG04 in the configuration`

## Side Effects
- `[sam_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[sam_boot.c:sam_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `sam_slcd_initialize()`, `sam_spidev_initialize()`)
- `[sam_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[sam_buttons.c:board_button_initialize]` Modifies interrupt controller or critical-section state
- `[sam_mmcsd.c:sam_sdinitialize]` Initializes/registers kernel devices or filesystems (`sam_spibus_initialize()`)
- `[sam_slcd.c:sam_slcd_initialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[sam_slcd.c:sam_slcd_initialize]` Configures or drives hardware GPIO pins
- `[sam_slcd.c:sam_slcd_initialize]` Initializes/registers kernel devices or filesystems (`register_driver()`)
- `[sam_spi.c:sam_spidev_initialize]` Configures or drives hardware GPIO pins
- `[sam_ug2832hsweg04.c:board_graphics_setup]` Configures or drives hardware GPIO pins
- `[sam_ug2832hsweg04.c:board_graphics_setup]` Initializes/registers kernel devices or filesystems (`sam_spibus_initialize()`, `ssd1306_initialize()`)
- `[sam_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh sam4l-xplained:nsh && make`
