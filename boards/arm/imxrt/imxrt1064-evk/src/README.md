# `imxrt1064-evk/src` Component (`boards/arm/imxrt/imxrt1064-evk/src`)

## Overview
Board-level C implementation (`src`) for `imxrt1064-evk` (`arm/imxrt`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 24 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[imxrt1064-evk.h:imxrt_bringup]` Public declaration `imxrt_bringup()`
- `[imxrt1064-evk.h:imxrt_spidev_initialize]` Public declaration `imxrt_spidev_initialize()`
- `[imxrt1064-evk.h:imxrt_mmcsd_spi_initialize]` Public declaration `imxrt_mmcsd_spi_initialize()`
- `[imxrt1064-evk.h:imxrt_gpio_initialize]` Public declaration `imxrt_gpio_initialize()`
- `[imxrt1064-evk.h:imxrt_can_setup]` Public declaration `imxrt_can_setup()`
- `[imxrt1064-evk.h:imxrt_adc_initialize]` Public declaration `imxrt_adc_initialize()`
- `[imxrt1064-evk.h:imxrt_ft5x06_register]` Public declaration `imxrt_ft5x06_register()`
- `[imxrt1064-evk.h:imxrt_lcd_initialize]` Public declaration `imxrt_lcd_initialize()`
- `[imxrt1064-evk.h:imxrt_usbhost_initialize]` Public declaration `imxrt_usbhost_initialize()`
- `[imxrt1064-evk.h:imxrt_flexspi_nor_initialize]` Public declaration `imxrt_flexspi_nor_initialize()`
- `[imxrt1064-evk.h:imxrt_progmem_init]` Public declaration `imxrt_progmem_init()`
- `[imxrt1064-evk.h:HAVE_PROGMEM_CHARDEV]` Hardware/board configuration macros (`HAVE_PROGMEM_CHARDEV`, `FT5X06_I2C_ADDRESS`, `GPIO_LED`, `LED_DRIVER_PATH`, `GPIO_SW8`, `GPIO_SW8_INT` (+21 more))
- `[imxrt_flexspi_nor_boot.h:ivt_s]` Type definition `ivt_s`
- `[imxrt_flexspi_nor_boot.h:boot_data_s]` Type definition `boot_data_s`
- `[imxrt_flexspi_nor_boot.h:IVT_MAJOR_VERSION]` Hardware/board configuration macros (`IVT_MAJOR_VERSION`, `IVT_MAJOR_VERSION_SHIFT`, `IVT_MAJOR_VERSION_MASK`, `IVT_MINOR_VERSION`, `IVT_MINOR_VERSION_SHIFT`, `IVT_MINOR_VERSION_MASK` (+27 more))
- `[imxrt_flexspi_nor_flash.h:flexspi_serial_clkfreq_e]` Type definition `flexspi_serial_clkfreq_e`
- `[imxrt_flexspi_nor_flash.h:flexspi_serial_clockmode_e]` Type definition `flexspi_serial_clockmode_e`
- `[imxrt_flexspi_nor_flash.h:flash_read_sample_clk_e]` Type definition `flash_read_sample_clk_e`
- `[imxrt_flexspi_nor_flash.h:flash_misc_feature_e]` Type definition `flash_misc_feature_e`
- `[imxrt_flexspi_nor_flash.h:flash_flash_type_e]` Type definition `flash_flash_type_e`
- `[imxrt_flexspi_nor_flash.h:flash_flash_pad_e]` Type definition `flash_flash_pad_e`
- `[imxrt_flexspi_nor_flash.h:flash_config_cmd_e]` Type definition `flash_config_cmd_e`
- `[imxrt_flexspi_nor_flash.h:flexspi_lut_seq_s]` Type definition `flexspi_lut_seq_s`
- *(+53 additional symbols across 24 files)*

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_BOARDCTL_BOOT_IMAGE`, `CONFIG_BOARDCTL_RESET`, `CONFIG_DEV_GPIO`, `CONFIG_IMXRT1064_EVK_SDRAM` (+11 more)
- `[imxrt_adc.c:imxrt_adc_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[imxrt_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[imxrt_ethernet.c:DEBUGASSERT]` Requires `intf`
- `[imxrt_flexcan.c:imxrt_can_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[imxrt_flexspi_nor.c:imxrt_flexspi_nor_initialize]` Validates preconditions and returns `-EINVAL`, `-EIO`, `-ENOTTY` on failure
- `[imxrt_flexspi_nor_flash.c:#error]` Compile-time guard: `Boot Flash type not chosen!`
- `[imxrt_ft5x06.c:DEBUGASSERT]` Requires `irq > 0 && irq < UINT8_MAX`
- `[imxrt_gpio.c:DEBUGASSERT]` Requires `imxrtgpio != NULL && value != NULL`
- `[imxrt_gpio.c:DEBUGASSERT]` Requires `imxrtgpio->id < BOARD_NGPIOIN`
- `[imxrt_mmcsd_spi.c:#error]` Compile-time guard: `SD driver requires CONFIG_IMXRT_LPSPI1 to be enabled`
- `[imxrt_mmcsd_spi.c:#error]` Compile-time guard: `SD driver requires CONFIG_DISABLE_MOUNTPOINT to be disabled`

## Side Effects
- `[imxrt1064-evk.h:imxrt_bringup]` Initializes/registers kernel devices or filesystems (`imxrt_autoled_initialize()`)
- `[imxrt_adc.c:imxrt_adc_initialize]` Initializes/registers kernel devices or filesystems (`adc_register()`)
- `[imxrt_boot.c:imxrt_ocram_initialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[imxrt_boot.c:imxrt_ocram_initialize]` Initializes/registers kernel devices or filesystems (`imxrt_autoled_initialize()`, `userled_lower_initialize()`)
- `[imxrt_boot_image.c:board_boot_image]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[imxrt_bringup.c:imxrt_bringup]` Initializes/registers kernel devices or filesystems (`board_button_initialize()`, `btn_lower_initialize()`, `fb_register()`, `i2c_register()`, `imxrt_adc_initialize()`)
- `[imxrt_buttons.c:board_button_initialize]` Modifies interrupt controller or critical-section state
- `[imxrt_ethernet.c:imxrt_phy_boardinitialize]` Modifies interrupt controller or critical-section state
- `[imxrt_flexspi_nor.c:imxrt_flexspi_nor_initialize]` Initializes/registers kernel devices or filesystems (`imxrt_flexspi_initialize()`, `nx_mount()`)
- `[imxrt_ft5x06.c:imxrt_ft5x06_register]` Initializes/registers kernel devices or filesystems (`ft5x06_register()`, `imxrt_i2cbus_initialize()`)
- `[imxrt_ft5x06.c:imxrt_ft5x06_register]` Modifies interrupt controller or critical-section state
- `[imxrt_gpio.c:imxrt_gpio_initialize]` Initializes/registers kernel devices or filesystems (`gpio_pin_register()`)

## Verification
- Run: `./tools/configure.sh imxrt1064-evk:nsh && make`
