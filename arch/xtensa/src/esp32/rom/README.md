# rom (`nuttx/arch/xtensa/src/esp32/rom`)

## Overview
Hardware abstraction and architecture package for `rom` under `nuttx/arch/xtensa/src/esp32/rom`, providing 3 header file(s) and 0 source file(s) (including `esp32_efuse.h`, `esp32_libc_stubs.h`, `esp32_spiflash.h`).

## Interface
- `[esp32_efuse.h:ets_efuse_read_op]`
- `[esp32_efuse.h:ets_efuse_program_op]`
- `[esp32_efuse.h:ets_efuse_get_8m_clock]`
- `[esp32_efuse.h:ets_efuse_get_spiconfig]`
- `[esp32_efuse.h:esp_crc8]`
- `[esp32_efuse.h:EFUSE_SPICFG_SPI_DEFAULTS]`
- `[esp32_efuse.h:EFUSE_SPICFG_HSPI_DEFAULTS]`
- `[esp32_efuse.h:EFUSE_SPICFG_RET_SPICLK_MASK]`
- `[esp32_efuse.h:EFUSE_SPICFG_RET_SPICLK_SHIFT]`
- `[esp32_efuse.h:EFUSE_SPICFG_RET_SPICLK]`
- `[esp32_efuse.h:EFUSE_SPICFG_RET_SPIQ_MASK]`
- `[esp32_efuse.h:EFUSE_SPICFG_RET_SPIQ_SHIFT]`
- `[esp32_efuse.h:EFUSE_SPICFG_RET_SPIQ]`
- `[esp32_efuse.h:EFUSE_SPICFG_RET_SPID_MASK]`
- `[esp32_efuse.h:EFUSE_SPICFG_RET_SPID_SHIFT]`
- `[esp32_efuse.h:EFUSE_SPICFG_RET_SPID]`
- `[esp32_efuse.h:EFUSE_SPICFG_RET_SPICS0_MASK]`
- `[esp32_libc_stubs.h:esp_setup_syscall_table]`
- `[esp32_libc_stubs.h:syscall_stub_table]`
- `[esp32_libc_stubs.h:_lock_t]`
- `[esp32_spiflash.h:esp_rom_spiflash_fix_dummylen]`
- `[esp32_spiflash.h:esp_rom_spiflash_select_qiomode]`
- `[esp32_spiflash.h:esp_rom_spiflash_set_drvs]`
- `[esp32_spiflash.h:esp_rom_spiflash_select_padsfunc]`
- `[esp32_spiflash.h:esp_rom_spiflash_attach]`
- `[esp32_spiflash.h:esp_rom_spiflash_read_status]`
- `[esp32_spiflash.h:esp_rom_spiflash_read_statushigh]`
- `[esp32_spiflash.h:esp32_spiflash_write_status]`
- `[esp32_spiflash.h:esp_rom_spiflash_read_user_cmd]`
- `[esp32_spiflash.h:esp_rom_spiflash_config_readmode]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
