# `fmu-v6xrt/src` Component (`boards/arm/imxrt/fmu-v6xrt/src`)

## Overview
Board-level C implementation (`src`) for `fmu-v6xrt` (`arm/imxrt`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 9 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[fmu-v6xrt.h:imxrt_bringup]` Public declaration `imxrt_bringup()`
- `[fmu-v6xrt.h:imxrt_spidev_initialize]` Public declaration `imxrt_spidev_initialize()`
- `[fmu-v6xrt.h:imxrt_mmcsd_spi_initialize]` Public declaration `imxrt_mmcsd_spi_initialize()`
- `[fmu-v6xrt.h:imxrt_gpio_initialize]` Public declaration `imxrt_gpio_initialize()`
- `[fmu-v6xrt.h:imxrt_can_setup]` Public declaration `imxrt_can_setup()`
- `[fmu-v6xrt.h:imxrt_adc_initialize]` Public declaration `imxrt_adc_initialize()`
- `[fmu-v6xrt.h:imxrt_ft5x06_register]` Public declaration `imxrt_ft5x06_register()`
- `[fmu-v6xrt.h:imxrt_lcd_initialize]` Public declaration `imxrt_lcd_initialize()`
- `[fmu-v6xrt.h:imxrt_usbhost_initialize]` Public declaration `imxrt_usbhost_initialize()`
- `[fmu-v6xrt.h:imxrt_flexspi_nor_initialize]` Public declaration `imxrt_flexspi_nor_initialize()`
- `[fmu-v6xrt.h:imxrt_flexspi_fram_initialize]` Public declaration `imxrt_flexspi_fram_initialize()`
- `[fmu-v6xrt.h:imxrt_cm4_initialize]` Public declaration `imxrt_cm4_initialize()`
- `[fmu-v6xrt.h:GT911_I2C_ADDRESS]` Hardware/board configuration macros (`GT911_I2C_ADDRESS`, `GPIO_LED1`, `GPIO_LED2`, `LED_DRIVER_PATH`, `GPIO_SW7`, `GPIO_SW7_INT` (+23 more))
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
- *(+15 additional symbols across 9 files)*

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_BOARDCTL`, `CONFIG_BOARD_LATE_INITIALIZE`, `CONFIG_FMU_V6XRT_CM4_ROMFS`, `CONFIG_IMXRT_RPTUN`

## Side Effects
- `[fmu-v6xrt.h:imxrt_bringup]` Initializes/registers kernel devices or filesystems (`imxrt_autoled_initialize()`)
- `[imxrt_boot.c:imxrt_ocram_initialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[imxrt_boot.c:imxrt_ocram_initialize]` Initializes/registers kernel devices or filesystems (`imxrt_autoled_initialize()`)
- `[imxrt_bringup.c:imxrt_bringup]` Initializes/registers kernel devices or filesystems (`btn_lower_initialize()`, `fb_register()`, `i2c_register()`, `imxrt_adc_initialize()`, `imxrt_cm4_initialize()`)

## Verification
- Run: `./tools/configure.sh fmu-v6xrt:nsh && make`
