# `rddrone-bms772/src` Component (`boards/arm/s32k1xx/rddrone-bms772/src`)

## Overview
Board-level C implementation (`src`) for `rddrone-bms772` (`arm/s32k1xx`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 16 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[rddrone-bms772.h:s32k1xx_bringup]` Public declaration `s32k1xx_bringup()`
- `[rddrone-bms772.h:s32k1xx_gpio_initialize]` Public declaration `s32k1xx_gpio_initialize()`
- `[rddrone-bms772.h:s32k1xx_i2cdev_initialize]` Public declaration `s32k1xx_i2cdev_initialize()`
- `[rddrone-bms772.h:s32k1xx_spidev_initialize]` Public declaration `s32k1xx_spidev_initialize()`
- `[rddrone-bms772.h:s32k1xx_nrstcheck_procfs_register]` Public declaration `s32k1xx_nrstcheck_procfs_register()`
- `[rddrone-bms772.h:GPIO_LED_R]` Hardware/board configuration macros (`GPIO_LED_R`, `GPIO_LED_G`, `GPIO_LED_B`, `GPIO0`, `GPIO1`, `GPIO2` (+10 more))
- `[etc_romfs.c:romfs_img]` Module symbol `romfs_img`
- `[s32k1xx_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[s32k1xx_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[s32k1xx_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[s32k1xx_boot.c:s32k1xx_board_initialize]` Public function `s32k1xx_board_initialize()`
- `[s32k1xx_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[s32k1xx_bringup.c:s32k1xx_bringup]` Public function `s32k1xx_bringup()`
- `[s32k1xx_clockconfig.c:g_initial_clkconfig]` Exported global symbol `g_initial_clkconfig`
- `[s32k1xx_gpio.c:s32k1xx_gpio_initialize]` Public function `s32k1xx_gpio_initialize()`
- `[s32k1xx_i2c.c:s32k1xx_i2cdev_initialize]` Public function `s32k1xx_i2cdev_initialize()`
- `[s32k1xx_nrstcheck_procfs.c:s32k1xx_nrstcheck_procfs_register]` Public function `s32k1xx_nrstcheck_procfs_register()`
- `[s32k1xx_periphclocks.c:g_peripheral_clockconfig0]` Exported global symbol `g_peripheral_clockconfig0`
- `[s32k1xx_reset.c:board_reset]` Public function `board_reset()`
- `[s32k1xx_smbus_sbd.c:smbus_sbd_initialize]` Public function `smbus_sbd_initialize()`
- `[s32k1xx_spi.c:s32k1xx_spidev_initialize]` Public function `s32k1xx_spidev_initialize()`
- `[s32k1xx_spi.c:s32k1xx_lpspi0status]` Public function `s32k1xx_lpspi0status()`
- `[s32k1xx_spi.c:s32k1xx_lpspi1status]` Public function `s32k1xx_lpspi1status()`
- *(+8 additional symbols across 16 files)*

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_LEDS`, `CONFIG_BOARDCTL_RESET`, `CONFIG_BOARDCTL_UNIQUEID`, `CONFIG_DEV_GPIO`, `CONFIG_ETC_ROMFS`, `CONFIG_LCD_SSD1306_I2C` (+4 more)
- `[s32k1xx_gpio.c:DEBUGASSERT]` Requires `s32k1xx_gpio != NULL && s32k1xx_gpio->callback != NULL`
- `[s32k1xx_gpio.c:DEBUGASSERT]` Requires `s32k1xx_gpio != NULL && value != NULL`
- `[s32k1xx_gpio.c:DEBUGASSERT]` Requires `s32k1xx_gpio->id < NUM_OF_GPIO`
- `[s32k1xx_i2c.c:s32k1xx_i2cdev_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[s32k1xx_nrstcheck_procfs.c:DEBUGASSERT]` Requires `attr`
- `[s32k1xx_nrstcheck_procfs.c:DEBUGASSERT]` Requires `oldattr`
- `[s32k1xx_smbus_sbd.c:DEBUGASSERT]` Requires `filep->f_inode->i_private`
- `[s32k1xx_smbus_sbd.c:DEBUGASSERT]` Requires `dev->refs > 0`
- `[s32k1xx_spi.c:s32k1xx_spidev_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[s32k1xx_ssd1306.c:board_lcd_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[s32k1xx_uid.c:#error]` Compile-time guard: `CONFIG_BOARDCTL_UNIQUEID_SIZE does not match S32K1XX_UID_SIZE`

## Side Effects
- `[s32k1xx_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[s32k1xx_boot.c:s32k1xx_board_initialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`)
- `[s32k1xx_bringup.c:s32k1xx_bringup]` Initializes/registers kernel devices or filesystems (`fb_register()`, `nx_mount()`, `progmem_initialize()`, `s32k1xx_eeeprom_register()`, `s32k1xx_gpio_initialize()`)
- `[s32k1xx_gpio.c:s32k1xx_gpio_initialize]` Configures or drives hardware GPIO pins
- `[s32k1xx_gpio.c:s32k1xx_gpio_initialize]` Initializes/registers kernel devices or filesystems (`gpio_pin_register()`)
- `[s32k1xx_i2c.c:s32k1xx_i2cdev_initialize]` Initializes/registers kernel devices or filesystems (`i2c_register()`, `s32k1xx_i2cbus_initialize()`)
- `[s32k1xx_nrstcheck_procfs.c:s32k1xx_nrstcheck_procfs_register]` Configures or drives hardware GPIO pins
- `[s32k1xx_nrstcheck_procfs.c:s32k1xx_nrstcheck_procfs_register]` Initializes/registers kernel devices or filesystems (`procfs_register()`)
- `[s32k1xx_smbus_sbd.c:smbus_sbd_initialize]` Initializes/registers kernel devices or filesystems (`register_driver()`)
- `[s32k1xx_smbus_sbd.c:smbus_sbd_initialize]` Modifies interrupt controller or critical-section state
- `[s32k1xx_spi.c:s32k1xx_spidev_initialize]` Configures or drives hardware GPIO pins
- `[s32k1xx_spi.c:s32k1xx_spidev_initialize]` Initializes/registers kernel devices or filesystems (`s32k1xx_lpspibus_initialize()`, `spi_register()`)

## Verification
- Run: `./tools/configure.sh rddrone-bms772:nsh && make`
