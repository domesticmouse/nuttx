# `icicle/include` Component (`boards/risc-v/mpfs/icicle/include`)

## Overview
Board-level public headers (`include`) for `icicle` (`risc-v/mpfs`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 4 header file(s).

## Interface
- `[board.h:mpfs_boardinitialize]` Public declaration `mpfs_boardinitialize()`
- `[board.h:MPFS_EMMC_CLK_MODE]` Hardware/board configuration macros (`MPFS_EMMC_CLK_MODE`, `MPFS_SD_CLOCK_4BIT`, `MPFS_MSS_EXT_SGMII_REF_CLK`, `MPFS_MSS_COREPLEX_CPU_CLK`, `MPFS_MSS_SYSTEM_CLK`, `MPFS_MSS_RTC_TOGGLE_CLK` (+28 more))
- `[board_liberodefs.h:LIBERO_SETTING_MSS_EXT_SGMII_REF_CLK]` Hardware/board configuration macros (`LIBERO_SETTING_MSS_EXT_SGMII_REF_CLK`, `LIBERO_SETTING_MSS_RTC_TOGGLE_CLK`, `LIBERO_SETTING_MSS_ENVM_CR`, `LIBERO_SETTING_MSS_CLOCK_CONFIG_CR`, `LIBERO_SETTING_MSS_MSSCLKMUX`, `LIBERO_SETTING_MSS_PLL_CKMUX` (+548 more))
- `[board_memorymap.h:MPFS_DDR_BASE]` Hardware/board configuration macros (`MPFS_DDR_BASE`, `MPFS_DDR_SIZE`, `KFLASH_START`, `KFLASH_SIZE`, `KSRAM_START`, `KSRAM_SIZE` (+10 more))
- `[boot_romfsimg.h]` Board header declarations `boot_romfsimg.h`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh icicle:nsh && make`
