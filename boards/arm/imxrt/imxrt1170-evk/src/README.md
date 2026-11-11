# `imxrt1170-evk/src` Component (`boards/arm/imxrt/imxrt1170-evk/src`)

## Overview
Board-level C implementation (`src`) for `imxrt1170-evk` (`arm/imxrt`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 23 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[imxrt1170-evk.h:imxrt_bringup]` Public declaration `imxrt_bringup()`
- `[imxrt1170-evk.h:imxrt_spidev_initialize]` Public declaration `imxrt_spidev_initialize()`
- `[imxrt1170-evk.h:imxrt_mmcsd_spi_initialize]` Public declaration `imxrt_mmcsd_spi_initialize()`
- `[imxrt1170-evk.h:imxrt_gpio_initialize]` Public declaration `imxrt_gpio_initialize()`
- `[imxrt1170-evk.h:imxrt_can_setup]` Public declaration `imxrt_can_setup()`
- `[imxrt1170-evk.h:imxrt_adc_initialize]` Public declaration `imxrt_adc_initialize()`
- `[imxrt1170-evk.h:imxrt_ft5x06_register]` Public declaration `imxrt_ft5x06_register()`
- `[imxrt1170-evk.h:imxrt_lcd_initialize]` Public declaration `imxrt_lcd_initialize()`
- `[imxrt1170-evk.h:imxrt_usbhost_initialize]` Public declaration `imxrt_usbhost_initialize()`
- `[imxrt1170-evk.h:imxrt_flexspi_nor_initialize]` Public declaration `imxrt_flexspi_nor_initialize()`
- `[imxrt1170-evk.h:imxrt_flexspi_fram_initialize]` Public declaration `imxrt_flexspi_fram_initialize()`
- `[imxrt1170-evk.h:GT911_I2C_ADDRESS]` Hardware/board configuration macros (`GT911_I2C_ADDRESS`, `GPIO_LED1`, `GPIO_LED2`, `LED_DRIVER_PATH`, `GPIO_SW7`, `GPIO_SW7_INT` (+23 more))
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
- *(+60 additional symbols across 23 files)*

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_DEV_GPIO`, `CONFIG_IMXRT1170_EVK_SDRAM`, `CONFIG_IMXRT1170_FLEXSPI_FRAM`, `CONFIG_IMXRT1170_FLEXSPI_NOR` (+9 more)
- `[imxrt_adc.c:imxrt_adc_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[imxrt_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[imxrt_ethernet.c:DEBUGASSERT]` Requires `intf`
- `[imxrt_flexcan.c:imxrt_can_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[imxrt_flexspi_fram.c:imxrt_flexspi_fram_initialize]` Validates preconditions and returns `-EINVAL`, `-EIO`, `-ENOTTY` on failure
- `[imxrt_flexspi_nor.c:imxrt_flexspi_nor_initialize]` Validates preconditions and returns `-EINVAL`, `-EIO`, `-ENOTTY` on failure
- `[imxrt_flexspi_nor_flash.c:#error]` Compile-time guard: `Boot Flash type not chosen!`
- `[imxrt_ft5x06.c:DEBUGASSERT]` Requires `irq > 0 && irq < UINT8_MAX`
- `[imxrt_gpio.c:DEBUGASSERT]` Requires `imxrtgpio != NULL && value != NULL`
- `[imxrt_gpio.c:DEBUGASSERT]` Requires `imxrtgpio->id < BOARD_NGPIOIN`
- `[imxrt_mmcsd_spi.c:#error]` Compile-time guard: `SD driver requires CONFIG_IMXRT_LPSPI1 to be enabled`

## Side Effects
- `[imxrt1170-evk.h:imxrt_bringup]` Initializes/registers kernel devices or filesystems (`imxrt_autoled_initialize()`)
- `[imxrt_adc.c:imxrt_adc_initialize]` Initializes/registers kernel devices or filesystems (`adc_register()`)
- `[imxrt_boot.c:imxrt_ocram_initialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[imxrt_boot.c:imxrt_ocram_initialize]` Initializes/registers kernel devices or filesystems (`imxrt_autoled_initialize()`, `userled_lower_initialize()`)
- `[imxrt_bringup.c:imxrt_bringup]` Initializes/registers kernel devices or filesystems (`btn_lower_initialize()`, `fb_register()`, `i2c_register()`, `imxrt_adc_initialize()`, `imxrt_flexspi_fram_initialize()`)
- `[imxrt_buttons.c:board_button_initialize]` Modifies interrupt controller or critical-section state
- `[imxrt_ethernet.c:imxrt_phy_boardinitialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[imxrt_ethernet.c:imxrt_phy_boardinitialize]` Modifies interrupt controller or critical-section state
- `[imxrt_flexspi_fram.c:imxrt_flexspi_fram_initialize]` Initializes/registers kernel devices or filesystems (`imxrt_flexspi_initialize()`, `nx_mount()`)
- `[imxrt_flexspi_nor.c:imxrt_flexspi_nor_initialize]` Initializes/registers kernel devices or filesystems (`imxrt_flexspi_initialize()`, `nx_mount()`)
- `[imxrt_ft5x06.c:imxrt_ft5x06_register]` Initializes/registers kernel devices or filesystems (`ft5x06_register()`, `imxrt_i2cbus_initialize()`)
- `[imxrt_ft5x06.c:imxrt_ft5x06_register]` Modifies interrupt controller or critical-section state

## Verification
- Run: `./tools/configure.sh imxrt1170-evk:nsh && make`
