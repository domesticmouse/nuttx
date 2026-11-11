# `lpc4088-devkit/src` Component (`boards/arm/lpc17xx_40xx/lpc4088-devkit/src`)

## Overview
Board-level C implementation (`src`) for `lpc4088-devkit` (`arm/lpc17xx_40xx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 13 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[lpc4088-devkit.h:lpc4088_devkit_bringup]` Public declaration `lpc4088_devkit_bringup()`
- `[lpc4088-devkit.h:lpc4088_devkit_sspdev_initialize]` Public declaration `lpc4088_devkit_sspdev_initialize()`
- `[lpc4088-devkit.h:lpc4088_devkit_sdram_initialize]` Public declaration `lpc4088_devkit_sdram_initialize()`
- `[lpc4088-devkit.h:lpc4088_devkit_nor_initialize]` Public declaration `lpc4088_devkit_nor_initialize()`
- `[lpc4088-devkit.h:lpc4088_devkit_nand_initialize]` Public declaration `lpc4088_devkit_nand_initialize()`
- `[lpc4088-devkit.h:lpc4088_devkit_lcd_initialize]` Public declaration `lpc4088_devkit_lcd_initialize()`
- `[lpc4088-devkit.h:lpc4088_devkit_tsc_setup]` Public declaration `lpc4088_devkit_tsc_setup()`
- `[lpc4088-devkit.h:lpc17_40_djoy_initialization]` Public declaration `lpc17_40_djoy_initialization()`
- `[lpc4088-devkit.h:GPIO_NAND_RB]` Hardware/board configuration macros (`GPIO_NAND_RB`, `GPIO_LED1`, `GPIO_LED2`, `GPIO_LED3`, `GPIO_LED4`, `GPIO_USER1` (+17 more))
- `[lpc17_40_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[lpc17_40_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[lpc17_40_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[lpc17_40_boardinitialize.c:lpc17_40_boardinitialize]` Public function `lpc17_40_boardinitialize()`
- `[lpc17_40_boardinitialize.c:board_late_initialize]` Public function `board_late_initialize()`
- `[lpc17_40_bringup.c:lpc4088_devkit_bringup]` Public function `lpc4088_devkit_bringup()`
- `[lpc17_40_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[lpc17_40_buttons.c:board_buttons]` Public function `board_buttons()`
- `[lpc17_40_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[lpc17_40_djoystick.c:lpc17_40_djoy_initialization]` Public function `lpc17_40_djoy_initialization()`
- `[lpc17_40_lcd.c:lpc4088_devkit_lcd_initialize]` Public function `lpc4088_devkit_lcd_initialize()`
- `[lpc17_40_lcd.c:lpc17_40_backlight]` Public function `lpc17_40_backlight()`
- `[lpc17_40_nandinitialize.c:lpc4088_devkit_nand_initialize]` Public function `lpc4088_devkit_nand_initialize()`
- `[lpc17_40_norinitialize.c:lpc4088_devkit_nor_initialize]` Public function `lpc4088_devkit_nor_initialize()`
- *(+12 additional symbols across 13 files)*

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_INPUT_ADS7843E`, `CONFIG_LPC17_40_EMC`, `CONFIG_LPC17_40_EXTDRAM`, `CONFIG_LPC17_40_EXTNAND` (+3 more)
- `[lpc17_40_bringup.c:lpc4088_devkit_bringup]` Validates preconditions and returns `-ENODEV`, `-ENOEXEC` on failure
- `[lpc17_40_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[lpc17_40_djoystick.c:DEBUGASSERT]` Requires `g_djoyhandler != NULL`
- `[lpc17_40_touchscreen.c:DEBUGASSERT]` Requires `minor == 0`
- `[lpc17_40_touchscreen.c:#error]` Compile-time guard: `Touchscreen support requires CONFIG_INPUT`
- `[lpc17_40_touchscreen.c:#error]` Compile-time guard: `Touchscreen support requires CONFIG_LPC17_40_SSP1`

## Side Effects
- `[lpc17_40_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[lpc17_40_boardinitialize.c:lpc17_40_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `lpc4088_devkit_lcd_initialize()`, `lpc4088_devkit_nand_initialize()`, `lpc4088_devkit_nor_initialize()`, `lpc4088_devkit_sdram_initialize()`)
- `[lpc17_40_bringup.c:lpc4088_devkit_bringup]` Configures or drives hardware GPIO pins
- `[lpc17_40_bringup.c:lpc4088_devkit_bringup]` Initializes/registers kernel devices or filesystems (`fb_register()`, `lpc17_40_usbhost_initialize()`, `nx_mount()`, `sdio_initialize()`, `usbhost_cdcacm_initialize()`)
- `[lpc17_40_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[lpc17_40_buttons.c:board_button_initialize]` Modifies interrupt controller or critical-section state
- `[lpc17_40_djoystick.c:lpc17_40_djoy_initialization]` Configures or drives hardware GPIO pins
- `[lpc17_40_djoystick.c:lpc17_40_djoy_initialization]` Initializes/registers kernel devices or filesystems (`djoy_register()`)
- `[lpc17_40_djoystick.c:lpc17_40_djoy_initialization]` Modifies interrupt controller or critical-section state
- `[lpc17_40_lcd.c:lpc4088_devkit_lcd_initialize]` Configures or drives hardware GPIO pins
- `[lpc17_40_nandinitialize.c:lpc4088_devkit_nand_initialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[lpc17_40_norinitialize.c:lpc4088_devkit_nor_initialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)

## Verification
- Run: `./tools/configure.sh lpc4088-devkit:nsh && make`
