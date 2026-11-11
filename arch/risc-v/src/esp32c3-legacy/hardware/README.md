# hardware (`nuttx/arch/risc-v/src/esp32c3-legacy/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/risc-v/src/esp32c3-legacy/hardware`, providing 39 header file(s) and 0 source file(s) (including `apb_ctrl_reg.h`, `bb_reg.h`, `esp32c3_aes.h`, `esp32c3_cache_memory.h`).

## Interface
- `[apb_ctrl_reg.h:APB_CTRL_FRONT_END_MEM_PD_REG]`
- `[apb_ctrl_reg.h:APB_CTRL_MEM_POWER_UP_REG]`
- `[apb_ctrl_reg.h:APB_CTRL_RETENTION_CTRL_REG]`
- `[apb_ctrl_reg.h:APB_CTRL_DC_MEM_FORCE_PU]`
- `[apb_ctrl_reg.h:APB_CTRL_DC_MEM_FORCE_PU_M]`
- `[apb_ctrl_reg.h:APB_CTRL_DC_MEM_FORCE_PU_V]`
- `[apb_ctrl_reg.h:APB_CTRL_DC_MEM_FORCE_PU_S]`
- `[apb_ctrl_reg.h:APB_CTRL_PBUS_MEM_FORCE_PU]`
- `[apb_ctrl_reg.h:APB_CTRL_PBUS_MEM_FORCE_PU_M]`
- `[apb_ctrl_reg.h:APB_CTRL_PBUS_MEM_FORCE_PU_V]`
- `[apb_ctrl_reg.h:APB_CTRL_PBUS_MEM_FORCE_PU_S]`
- `[apb_ctrl_reg.h:APB_CTRL_AGC_MEM_FORCE_PU]`
- `[bb_reg.h:BBPD_CTRL]`
- `[bb_reg.h:BB_FFT_FORCE_PU]`
- `[bb_reg.h:BB_FFT_FORCE_PU_M]`
- `[bb_reg.h:BB_FFT_FORCE_PU_V]`
- `[bb_reg.h:BB_FFT_FORCE_PU_S]`
- `[bb_reg.h:BB_DC_EST_FORCE_PU]`
- `[bb_reg.h:BB_DC_EST_FORCE_PU_M]`
- `[bb_reg.h:BB_DC_EST_FORCE_PU_V]`
- `[bb_reg.h:BB_DC_EST_FORCE_PU_S]`
- `[esp32c3_aes.h:AES_KEY_0_REG]`
- `[esp32c3_aes.h:AES_KEY_0]`
- `[esp32c3_aes.h:AES_KEY_0_M]`
- `[esp32c3_aes.h:AES_KEY_0_V]`
- `[esp32c3_aes.h:AES_KEY_0_S]`
- `[esp32c3_aes.h:AES_KEY_1_REG]`
- `[esp32c3_aes.h:AES_KEY_1]`
- `[esp32c3_aes.h:AES_KEY_1_M]`
- `[esp32c3_aes.h:AES_KEY_1_V]`

## Invariants
- None

## Side Effects
- `[esp32c3_soc.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[esp32c3_soc.h:modifyreg32]` Performs atomic read-modify-write updates on 32-bit MMIO registers

## Verification
- Run: `make test`
