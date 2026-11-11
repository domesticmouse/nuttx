# `ddcnc-ec300/src` Component (`boards/arm/imxrt/ddcnc-ec300/src`)

## Overview
Board-level C implementation (`src`) for `ddcnc-ec300` (`arm/imxrt`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 10 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[ddcnc-ec300.h:imxrt_bringup]` Public declaration `imxrt_bringup()`
- `[ddcnc-ec300.h:imxrt_autoled_initialize]` Public declaration `imxrt_autoled_initialize()`
- `[ddcnc-ec300.h:GPIO_LED]` Hardware/board configuration macros (`GPIO_LED`)
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
- `[imxrt_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[imxrt_boot.c:imxrt_boardinitialize]` Public function `imxrt_boardinitialize()`
- `[imxrt_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[imxrt_bringup.c:imxrt_bringup]` Public function `imxrt_bringup()`
- *(+7 additional symbols across 10 files)*

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_LEDS`, `CONFIG_IMXRT_ENET`
- `[imxrt_ethernet.c:DEBUGASSERT]` Requires `intf`

## Side Effects
- `[imxrt_boot.c:imxrt_boardinitialize]` Initializes/registers kernel devices or filesystems (`imxrt_autoled_initialize()`)
- `[imxrt_bringup.c:imxrt_bringup]` Initializes/registers kernel devices or filesystems (`nx_mount()`)
- `[imxrt_ethernet.c:arch_phy_irq]` Modifies interrupt controller or critical-section state

## Verification
- Run: `./tools/configure.sh ddcnc-ec300:nsh && make`
