# `lpcxpresso-lpc54628/src` Component (`boards/arm/lpc54xx/lpcxpresso-lpc54628/src`)

## Overview
Board-level C implementation (`src`) for `lpcxpresso-lpc54628` (`arm/lpc54xx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 11 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[lpcxpresso-lpc54628.h:lpc54_bringup]` Public declaration `lpc54_bringup()`
- `[lpcxpresso-lpc54628.h:lpc54_sdram_initialize]` Public declaration `lpc54_sdram_initialize()`
- `[lpcxpresso-lpc54628.h:lpc54_lcd_initialize]` Public declaration `lpc54_lcd_initialize()`
- `[lpcxpresso-lpc54628.h:lpc54_i2ctool]` Public declaration `lpc54_i2ctool()`
- `[lpcxpresso-lpc54628.h:lpc54_ft5x06_register]` Public declaration `lpc54_ft5x06_register()`
- `[lpcxpresso-lpc54628.h:lpc54_i2c_handle]` Public declaration `lpc54_i2c_handle()`
- `[lpcxpresso-lpc54628.h:lpc54_i2c_free]` Public declaration `lpc54_i2c_free()`
- `[lpcxpresso-lpc54628.h:HAVE_I2CTOOL]` Hardware/board configuration macros (`HAVE_I2CTOOL`, `HAVE_MMCSD`, `HAVE_RTC_DRIVER`, `MMCSD_MINOR`, `I2C0NDX`, `I2C0CNT` (+29 more))
- `[lpc54_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[lpc54_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[lpc54_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[lpc54_boot.c:lpc54_board_initialize]` Public function `lpc54_board_initialize()`
- `[lpc54_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[lpc54_bringup.c:lpc54_bringup]` Public function `lpc54_bringup()`
- `[lpc54_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[lpc54_buttons.c:board_buttons]` Public function `board_buttons()`
- `[lpc54_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[lpc54_ft5x06.c:lpc54_ft5x06_register]` Public function `lpc54_ft5x06_register()`
- `[lpc54_i2c.c:lpc54_i2c_handle]` Public function `lpc54_i2c_handle()`
- `[lpc54_i2c.c:lpc54_i2c_free]` Public function `lpc54_i2c_free()`
- `[lpc54_i2ctool.c:lpc54_i2ctool]` Public function `lpc54_i2ctool()`
- `[lpc54_lcd.c:lpc54_lcd_initialize]` Public function `lpc54_lcd_initialize()`
- `[lpc54_lcd.c:lpc54_backlight]` Public function `lpc54_backlight()`
- *(+4 additional symbols across 11 files)*

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_INPUT_FT5X06`, `CONFIG_LPC54_EMC`, `CONFIG_LPC54_EMC_DYNAMIC`, `CONFIG_LPC54_HAVE_I2C_MASTER` (+1 more)
- `[lpc54_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[lpc54_ft5x06.c:DEBUGASSERT]` Requires `irq > 0 && irq < UINT8_MAX`

## Side Effects
- `[lpc54_boot.c:lpc54_board_initialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `lpc54_lcd_initialize()`, `lpc54_sdram_initialize()`)
- `[lpc54_bringup.c:lpc54_bringup]` Initializes/registers kernel devices or filesystems (`btn_lower_initialize()`, `fb_register()`, `lpc54_ft5x06_register()`, `lpc54_sdmmc_initialize()`, `nx_mount()`)
- `[lpc54_buttons.c:board_button_initialize]` Modifies interrupt controller or critical-section state
- `[lpc54_ft5x06.c:lpc54_ft5x06_register]` Initializes/registers kernel devices or filesystems (`ft5x06_register()`)
- `[lpc54_ft5x06.c:lpc54_ft5x06_register]` Modifies interrupt controller or critical-section state
- `[lpc54_i2c.c:lpc54_i2c_handle]` Initializes/registers kernel devices or filesystems (`lpc54_i2cbus_initialize()`)
- `[lpc54_i2ctool.c:lpc54_i2ctool]` Initializes/registers kernel devices or filesystems (`i2c_register()`, `lpc54_i2c_register()`)
- `[lpc54_sdram.c:lpc54_sdram_initialize]` Initializes/registers kernel devices or filesystems (`lpc54_emc_initialize()`, `lpc54_emc_sdram_initialize()`)

## Verification
- Run: `./tools/configure.sh lpcxpresso-lpc54628:nsh && make`
