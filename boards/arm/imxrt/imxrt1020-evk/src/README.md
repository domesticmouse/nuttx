# `imxrt1020-evk/src` Component (`boards/arm/imxrt/imxrt1020-evk/src`)

## Overview
Board-level C implementation (`src`) for `imxrt1020-evk` (`arm/imxrt`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 14 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[imxrt1020-evk.h:imxrt_bringup]` Public declaration `imxrt_bringup()`
- `[imxrt1020-evk.h:imxrt_spidev_initialize]` Public declaration `imxrt_spidev_initialize()`
- `[imxrt1020-evk.h:imxrt_mmcsd_spi_initialize]` Public declaration `imxrt_mmcsd_spi_initialize()`
- `[imxrt1020-evk.h:imxrt_autoled_initialize]` Public declaration `imxrt_autoled_initialize()`
- `[imxrt1020-evk.h:imxrt_gpio_initialize]` Public declaration `imxrt_gpio_initialize()`
- `[imxrt1020-evk.h:imxrt_usbhost_initialize]` Public declaration `imxrt_usbhost_initialize()`
- `[imxrt1020-evk.h:GPIO_USERLED]` Hardware/board configuration macros (`GPIO_USERLED`, `GPIO_SWWAKE`, `GPIO_ENET_INT`, `GPIO_ENET_IRQ`, `GPIO_ENET_RST`, `GPIO_USBOTG_ID` (+5 more))
- `[imxrt_flexspi_nor_boot.h:ivt_s]` Type definition `ivt_s`
- `[imxrt_flexspi_nor_boot.h:boot_data_s]` Type definition `boot_data_s`
- `[imxrt_flexspi_nor_boot.h:IVT_MAJOR_VERSION]` Hardware/board configuration macros (`IVT_MAJOR_VERSION`, `IVT_MAJOR_VERSION_SHIFT`, `IVT_MAJOR_VERSION_MASK`, `IVT_MINOR_VERSION`, `IVT_MINOR_VERSION_SHIFT`, `IVT_MINOR_VERSION_MASK` (+17 more))
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
- `[imxrt_autoleds.c:imxrt_autoled_initialize]` Public function `imxrt_autoled_initialize()`
- `[imxrt_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- *(+32 additional symbols across 14 files)*

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_DEV_GPIO`, `CONFIG_IMXRT_ENET`, `CONFIG_IMXRT_LPSPI`, `CONFIG_IMXRT_SDRAMC` (+1 more)
- `[imxrt_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure
- `[imxrt_ethernet.c:DEBUGASSERT]` Requires `intf`
- `[imxrt_flexspi_nor_flash.c:#error]` Compile-time guard: `Boot Flash type not chosen!`
- `[imxrt_gpio.c:DEBUGASSERT]` Requires `imxrtgpio != NULL && value != NULL`
- `[imxrt_gpio.c:DEBUGASSERT]` Requires `imxrtgpio->id < BOARD_NGPIOIN`
- `[imxrt_spi.c:imxrt_spidev_initialize]` Validates preconditions and returns `-ENODEV` on failure
- `[imxrt_usbhost.c:imxrt_usbhost_initialize]` Validates preconditions and returns `-ENODEV` on failure

## Side Effects
- `[imxrt_boot.c:imxrt_boardinitialize]` Initializes/registers kernel devices or filesystems (`imxrt_autoled_initialize()`)
- `[imxrt_bringup.c:imxrt_bringup]` Initializes/registers kernel devices or filesystems (`i2c_register()`, `imxrt_gpio_initialize()`, `imxrt_i2c_register()`, `imxrt_i2cbus_initialize()`, `imxrt_spi_register()`)
- `[imxrt_buttons.c:board_button_initialize]` Modifies interrupt controller or critical-section state
- `[imxrt_ethernet.c:imxrt_phy_boardinitialize]` Modifies interrupt controller or critical-section state
- `[imxrt_gpio.c:imxrt_gpio_initialize]` Initializes/registers kernel devices or filesystems (`gpio_pin_register()`)
- `[imxrt_usbhost.c:imxrt_usbhost_initialize]` Initializes/registers kernel devices or filesystems (`imxrt_ehci_initialize()`, `usbhost_cdcacm_initialize()`, `usbhost_hub_initialize()`, `usbhost_msc_initialize()`)
- `[imxrt_usbhost.c:imxrt_usbhost_initialize]` Modifies interrupt controller or critical-section state

## Verification
- Run: `./tools/configure.sh imxrt1020-evk:nsh && make`
