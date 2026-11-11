# `gd-xd-w515-eval/src` Component (`boards/arm/gd32w51x/gd-xd-w515-eval/src`)

## Overview
Board-level C implementation (`src`) for `gd-xd-w515-eval` (`arm/gd32w51x`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 11 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[gd-xd-w515-eval.h:gd32_bringup]` Public declaration `gd32_bringup()`
- `[gd-xd-w515-eval.h:gd32_spidev_initialize]` Public declaration `gd32_spidev_initialize()`
- `[gd-xd-w515-eval.h:gd32_gpio_initialize]` Public declaration `gd32_gpio_initialize()`
- `[gd-xd-w515-eval.h:gd32_qspixip_install]` Public declaration `gd32_qspixip_install()`
- `[gd-xd-w515-eval.h:gd32_qspixip_initialize]` Public declaration `gd32_qspixip_initialize()`
- `[gd-xd-w515-eval.h:GD32_CHARGER_I2C_FREQUENCY]` Hardware/board configuration macros (`GD32_CHARGER_I2C_FREQUENCY`, `GD32_CHARGER_ISET_CURRENT`)
- `[gd32_appinit.c:board_app_initialize]` Public function `board_app_initialize()`
- `[gd32_boot.c:gd32w51x_boardinitialize]` Public function `gd32w51x_boardinitialize()`
- `[gd32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[gd32_bringup.c:gd32_bringup]` Public function `gd32_bringup()`
- `[gd32_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[gd32_buttons.c:board_buttons]` Public function `board_buttons()`
- `[gd32_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[gd32_gpio.c:gd32_gpio_initialize]` Public function `gd32_gpio_initialize()`
- `[gd32_lcd.c:board_lcd_initialize]` Public function `board_lcd_initialize()`
- `[gd32_lcd.c:board_lcd_getdev]` Public function `board_lcd_getdev()`
- `[gd32_lcd.c:board_lcd_uninitialize]` Public function `board_lcd_uninitialize()`
- `[gd32_qspixip.c:gd32_qspixip_install]` Public function `gd32_qspixip_install()`
- `[gd32_qspixip.c:gd32_qspixip_initialize]` Public function `gd32_qspixip_initialize()`
- `[gd32_reset.c:board_reset]` Public function `board_reset()`
- `[gd32_spi.c:gd32_spidev_initialize]` Public function `gd32_spidev_initialize()`
- `[gd32_spi.c:gd32_spi0select]` Public function `gd32_spi0select()`
- `[gd32_spi.c:gd32_spi0status]` Public function `gd32_spi0status()`
- *(+9 additional symbols across 11 files)*

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_BUTTONS`, `CONFIG_BOARDCTL`, `CONFIG_BOARDCTL_RESET`, `CONFIG_DEV_GPIO`, `CONFIG_GD32W51X_SPI`, `CONFIG_GD_XD_W515_EVAL_QSPI_XIP` (+2 more)
- `[gd32_buttons.c:#error]` Compile-time guard: `The touch key needs CONFIG_GD32W51X_TSI`
- `[gd32_buttons.c:#error]` Compile-time guard: `The touch key needs a work queue`
- `[gd32_gpio.c:DEBUGASSERT]` Requires `gd32gpio->id < BOARD_NGPIOOUT && value != NULL`
- `[gd32_gpio.c:DEBUGASSERT]` Requires `gd32gpio->id < BOARD_NGPIOOUT`
- `[gd32_gpio.c:DEBUGASSERT]` Requires `gd32gpint->gd32gpio.id < BOARD_NGPIOINT && value != NULL`
- `[gd32_lcd.c:board_lcd_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[gd32_qspixip.c:gd32_qspixip_install]` Validates preconditions and returns `-EINVAL`, `-EIO`, `-EVAL` on failure
- `[gd32_spi.c:gd32_spidev_initialize]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[gd32_bringup.c:gd32_bringup]` Initializes/registers kernel devices or filesystems (`adc_register()`, `battery_charger_register()`, `btn_lower_initialize()`, `fb_register()`, `gd25_initialize()`)
- `[gd32_bringup.c:gd32_bringup]` Modifies interrupt controller or critical-section state
- `[gd32_buttons.c:board_button_initialize]` Initializes/registers kernel devices or filesystems (`gd32_tsi_initialize()`)
- `[gd32_buttons.c:board_button_initialize]` Modifies interrupt controller or critical-section state
- `[gd32_gpio.c:gd32_gpio_initialize]` Initializes/registers kernel devices or filesystems (`gpio_pin_register()`)
- `[gd32_lcd.c:board_lcd_initialize]` Initializes/registers kernel devices or filesystems (`gd32_spibus_initialize()`, `gd32_spidev_initialize()`)
- `[gd32_qspixip.c:gd32_qspixip_install]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)

## Verification
- Run: `./tools/configure.sh gd-xd-w515-eval:nsh && make`
