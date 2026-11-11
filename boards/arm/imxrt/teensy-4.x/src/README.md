# `teensy-4.x/src` Component (`boards/arm/imxrt/teensy-4.x/src`)

## Overview
Board-level C implementation (`src`) for `teensy-4.x` (`arm/imxrt`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 19 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
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
- `[imxrt_flexspi_nor_flash.h:flexspi_mem_config_s]` Type definition `flexspi_mem_config_s`
- `[imxrt_flexspi_nor_flash.h:flexspi_nor_config_s]` Type definition `flexspi_nor_config_s`
- `[imxrt_flexspi_nor_flash.h:FLEXSPI_CFG_BLK_TAG]` Hardware/board configuration macros (`FLEXSPI_CFG_BLK_TAG`, `FLEXSPI_CFG_BLK_VERSION`, `FLEXSPI_CFG_BLK_SIZE`, `FLEXSPI_FEATURE_HAS_PARALLEL_MODE`, `CMD_INDEX_READ`, `CMD_INDEX_READSTATUS` (+77 more))
- `[teensy-4.h:imxrt_bringup]` Public declaration `imxrt_bringup()`
- `[teensy-4.h:imxrt_spidev_initialize]` Public declaration `imxrt_spidev_initialize()`
- `[teensy-4.h:imxrt_can_setup]` Public declaration `imxrt_can_setup()`
- `[teensy-4.h:imxrt_pwm_setup]` Public declaration `imxrt_pwm_setup()`
- `[teensy-4.h:imxrt_adc_initialize]` Public declaration `imxrt_adc_initialize()`
- `[teensy-4.h:imxrt_gpio_initialize]` Public declaration `imxrt_gpio_initialize()`
- `[teensy-4.h:imxrt_enc_initialize]` Public declaration `imxrt_enc_initialize()`
- `[teensy-4.h:imxrt_i2c_setup]` Public declaration `imxrt_i2c_setup()`
- `[teensy-4.h:imxrt_autoled_initialize]` Public declaration `imxrt_autoled_initialize()`
- *(+39 additional symbols across 19 files)*

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_LEDS`, `CONFIG_BOARDCTL_RESET`, `CONFIG_DEV_GPIO`, `CONFIG_IMXRT_ADC`, `CONFIG_IMXRT_ENC`, `CONFIG_IMXRT_ENET` (+5 more)
- `[imxrt_adc.c:imxrt_adc_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[imxrt_enc.c:imxrt_enc_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[imxrt_ethernet.c:DEBUGASSERT]` Requires `intf`
- `[imxrt_flexcan.c:imxrt_can_setup]` Validates preconditions and returns `-ENODEV` on failure
- `[imxrt_flexpwm.c:imxrt_pwminitialize]` Validates preconditions and returns `-ENODEV` on failure
- `[imxrt_flexspi_nor_flash.c:#error]` Compile-time guard: `Boot Flash type not chosen!`
- `[imxrt_gpio.c:DEBUGASSERT]` Requires `imxrtgpio != NULL && value != NULL`
- `[imxrt_gpio.c:DEBUGASSERT]` Requires `imxrtgpio->id < BOARD_NGPIOIN`
- `[imxrt_spi.c:imxrt_spidev_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[imxrt_st7789.c:board_lcd_initialize]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[imxrt_adc.c:imxrt_adc_initialize]` Initializes/registers kernel devices or filesystems (`adc_register()`)
- `[imxrt_boot.c:imxrt_ocram_initialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[imxrt_boot.c:imxrt_ocram_initialize]` Initializes/registers kernel devices or filesystems (`imxrt_autoled_initialize()`, `imxrt_spidev_initialize()`, `userled_lower_initialize()`)
- `[imxrt_bringup.c:imxrt_bringup]` Initializes/registers kernel devices or filesystems (`cdcacm_initialize()`, `fb_register()`, `imxrt_adc_initialize()`, `imxrt_enc_initialize()`, `imxrt_gpio_initialize()`)
- `[imxrt_ethernet.c:imxrt_phy_boardinitialize]` Modifies interrupt controller or critical-section state
- `[imxrt_flexpwm.c:imxrt_pwminitialize]` Initializes/registers kernel devices or filesystems (`pwm_register()`)
- `[imxrt_gpio.c:imxrt_gpio_initialize]` Initializes/registers kernel devices or filesystems (`gpio_pin_register()`)
- `[imxrt_i2c.c:imxrt_i2c_setup]` Initializes/registers kernel devices or filesystems (`bmp280_register()`, `i2c_register()`, `imxrt_i2c_register()`, `imxrt_i2cbus_initialize()`)
- `[imxrt_st7789.c:board_lcd_initialize]` Initializes/registers kernel devices or filesystems (`imxrt_lpspibus_initialize()`)

## Verification
- Run: `./tools/configure.sh teensy-4.x:can-4.1 && make`
