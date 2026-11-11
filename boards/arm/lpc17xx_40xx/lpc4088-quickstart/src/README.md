# `lpc4088-quickstart/src` Component (`boards/arm/lpc17xx_40xx/lpc4088-quickstart/src`)

## Overview
Board-level C implementation (`src`) for `lpc4088-quickstart` (`arm/lpc17xx_40xx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 10 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[lpc4088-quickstart.h:lpc4088_quickstart_bringup]` Public declaration `lpc4088_quickstart_bringup()`
- `[lpc4088-quickstart.h:lpc4088_quickstart_sdram_initialize]` Public declaration `lpc4088_quickstart_sdram_initialize()`
- `[lpc4088-quickstart.h:lpc4088_quickstart_flash_initialize]` Public declaration `lpc4088_quickstart_flash_initialize()`
- `[lpc4088-quickstart.h:GPIO_LED1]` Hardware/board configuration macros (`GPIO_LED1`, `GPIO_LED2`, `GPIO_LED3`, `GPIO_LED4`, `GPIO_USER1`, `GPIO_USER2_IRQ`)
- `[lpc17_40_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[lpc17_40_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[lpc17_40_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[lpc17_40_boardinitialize.c:lpc17_40_boardinitialize]` Public function `lpc17_40_boardinitialize()`
- `[lpc17_40_boardinitialize.c:board_late_initialize]` Public function `board_late_initialize()`
- `[lpc17_40_bringup.c:lpc4088_quickstart_bringup]` Public function `lpc4088_quickstart_bringup()`
- `[lpc17_40_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[lpc17_40_buttons.c:board_buttons]` Public function `board_buttons()`
- `[lpc17_40_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[lpc17_40_lcd.c:lpc4088_devkit_lcd_initialize]` Public function `lpc4088_devkit_lcd_initialize()`
- `[lpc17_40_lcd.c:lpc17_40_backlight]` Public function `lpc17_40_backlight()`
- `[lpc17_40_nandinitialize.c:_lpc4088_quickstart_nand_initialize]` Public function `_lpc4088_quickstart_nand_initialize()`
- `[lpc17_40_sdraminitialize.c:lpc4088_quickstart_sdram_initialize]` Public function `lpc4088_quickstart_sdram_initialize()`
- `[lpc17_40_ssp.c:lpc4088_quickstart_sspdev_initialize]` Public function `lpc4088_quickstart_sspdev_initialize()`
- `[lpc17_40_ssp.c:lpc17_40_ssp0select]` Public function `lpc17_40_ssp0select()`
- `[lpc17_40_ssp.c:lpc17_40_ssp0status]` Public function `lpc17_40_ssp0status()`
- `[lpc17_40_ssp.c:lpc17_40_ssp1select]` Public function `lpc17_40_ssp1select()`
- `[lpc17_40_ssp.c:lpc17_40_ssp1status]` Public function `lpc17_40_ssp1status()`
- `[lpc17_40_ssp.c:lpc17_40_ssp2select]` Public function `lpc17_40_ssp2select()`
- *(+4 additional symbols across 10 files)*

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_LPC17_40_EMC`, `CONFIG_LPC17_40_EXTDRAM`, `CONFIG_LPC17_40_EXTNAND`, `CONFIG_LPC17_40_LCD`
- `[lpc17_40_bringup.c:lpc4088_quickstart_bringup]` Validates preconditions and returns `-ENODEV`, `-ENOEXEC` on failure
- `[lpc17_40_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure

## Side Effects
- `[lpc17_40_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[lpc17_40_boardinitialize.c:lpc17_40_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `lpc4088_quickstart_flash_initialize()`, `lpc4088_quickstart_sdram_initialize()`, `lpc4088_quickstart_sspdev_initialize()`)
- `[lpc17_40_bringup.c:lpc4088_quickstart_bringup]` Configures or drives hardware GPIO pins
- `[lpc17_40_bringup.c:lpc4088_quickstart_bringup]` Initializes/registers kernel devices or filesystems (`lpc17_40_usbhost_initialize()`, `nx_mount()`, `sdio_initialize()`, `usbhost_cdcacm_initialize()`, `usbhost_msc_initialize()`)
- `[lpc17_40_bringup.c:lpc4088_quickstart_bringup]` Modifies interrupt controller or critical-section state
- `[lpc17_40_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[lpc17_40_buttons.c:board_button_initialize]` Modifies interrupt controller or critical-section state
- `[lpc17_40_lcd.c:lpc4088_devkit_lcd_initialize]` Configures or drives hardware GPIO pins
- `[lpc17_40_nandinitialize.c:_lpc4088_quickstart_nand_initialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[lpc17_40_sdraminitialize.c:lpc4088_quickstart_sdram_initialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[lpc17_40_ssp.c:lpc4088_quickstart_sspdev_initialize]` Configures or drives hardware GPIO pins
- `[lpc17_40_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh lpc4088-quickstart:nsh && make`
