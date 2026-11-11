# `m100pfsevp/include` Component (`boards/risc-v/mpfs/m100pfsevp/include`)

## Overview
Board-level public headers (`include`) for `m100pfsevp` (`risc-v/mpfs`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s).

## Interface
- `[board.h:mpfs_boardinitialize]` Public declaration `mpfs_boardinitialize()`
- `[board.h:MPFS_EMMC_CLK_MODE]` Hardware/board configuration macros (`MPFS_EMMC_CLK_MODE`, `MPFS_SD_CLOCK_4BIT`, `MPFS_EMMCSD_GPIO`, `MPFS_MSS_EXT_SGMII_REF_CLK`, `MPFS_MSS_COREPLEX_CPU_CLK`, `MPFS_MSS_SYSTEM_CLK` (+5 more))
- `[board_liberodefs.h:LIBERO_SETTING_MSS_EXT_SGMII_REF_CLK]` Hardware/board configuration macros (`LIBERO_SETTING_MSS_EXT_SGMII_REF_CLK`, `LIBERO_SETTING_MSS_RTC_TOGGLE_CLK`, `LIBERO_SETTING_MSS_ENVM_CR`, `LIBERO_SETTING_MSS_CLOCK_CONFIG_CR`, `LIBERO_SETTING_MSS_MSSCLKMUX`, `LIBERO_SETTING_MSS_PLL_CKMUX` (+548 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh m100pfsevp:nsh && make`
