# config (`nuttx/arch/risc-v/src/gd32vw55x/gdwifi/config`)

## Overview
Hardware abstraction and architecture package for `config` under `nuttx/arch/risc-v/src/gd32vw55x/gdwifi/config`, providing 4 header file(s) and 0 source file(s) (including `app_cfg.h`, `build_config.h`, `lwipopts.h`, `platform_def.h`).

## Interface
- `[app_cfg.h:_APP_CFG_H_]`
- `[app_cfg.h:CONFIG_DEBUG_PRINT_ENABLE]`
- `[app_cfg.h:CONFIG_SNTP]`
- `[build_config.h:_GDWIFI_BUILD_CONFIG_SHIM_H_]`
- `[build_config.h:__LITTLE_ENDIAN]`
- `[build_config.h:__BIG_ENDIAN]`
- `[build_config.h:__BYTE_ORDER]`
- `[lwipopts.h:_GDWIFI_LWIPOPTS_SHIM_H_]`
- `[lwipopts.h:IOV_MAX]`
- `[lwipopts.h:SOCKLEN_T_DEFINED]`
- `[lwipopts.h:iovec]`
- `[lwipopts.h:SA_FAMILY_T_DEFINED]`
- `[lwipopts.h:LWIP_TIMEVAL_PRIVATE]`
- `[platform_def.h:_PLATFORM_DEF_H]`
- `[platform_def.h:PLATFORM_FPGA_32103_V7]`
- `[platform_def.h:PLATFORM_FPGA_32103_ULTRA]`
- `[platform_def.h:PLATFORM_ASIC_32103]`
- `[platform_def.h:CONFIG_PLATFORM]`
- `[platform_def.h:CONFIG_PLATFORM_ASIC]`
- `[platform_def.h:CONFIG_PLATFORM_FPGA]`
- `[platform_def.h:PLATFORM_BOARD_32VW55X_START]`
- `[platform_def.h:PLATFORM_BOARD_32VW55X_EVAL]`
- `[platform_def.h:PLATFORM_BOARD_32VW55X_F527]`
- `[platform_def.h:PLATFORM_BOARD_32VW55X_SONIC]`
- `[platform_def.h:CONFIG_BOARD]`

## Invariants
- `[platform_def.h:#error]` Compile-time guard: CONFIG_PLATFORM must be defined!

## Side Effects
- None

## Verification
- Run: `make test`
