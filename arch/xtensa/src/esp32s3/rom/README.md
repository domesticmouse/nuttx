# rom (`nuttx/arch/xtensa/src/esp32s3/rom`)

## Overview
Hardware abstraction and architecture package for `rom` under `nuttx/arch/xtensa/src/esp32s3/rom`, providing 2 header file(s) and 0 source file(s) (including `esp32s3_libc_stubs.h`, `esp32s3_spiflash.h`).

## Interface
- `[esp32s3_libc_stubs.h:esp_setup_syscall_table]`
- `[esp32s3_libc_stubs.h:syscall_stub_table]`
- `[esp32s3_libc_stubs.h:syscall_table_ptr_pro]`
- `[esp32s3_libc_stubs.h:syscall_table_ptr_app]`
- `[esp32s3_spiflash.h:esp_rom_spiflash_fix_dummylen]`
- `[esp32s3_spiflash.h:esp_rom_spiflash_select_qiomode]`
- `[esp32s3_spiflash.h:esp_rom_spiflash_set_drvs]`
- `[esp32s3_spiflash.h:esp_rom_spiflash_select_padsfunc]`
- `[esp32s3_spiflash.h:esp_rom_spiflash_attach]`
- `[esp32s3_spiflash.h:esp_rom_spiflash_read_status]`
- `[esp32s3_spiflash.h:esp32s3_spiflash_read_statushigh]`
- `[esp32s3_spiflash.h:esp32s3_spiflash_write_status]`
- `[esp32s3_spiflash.h:esp_rom_spiflash_read_user_cmd]`
- `[esp32s3_spiflash.h:esp_rom_spiflash_config_readmode]`
- `[esp32s3_spiflash.h:esp_rom_spiflash_config_clk]`
- `[esp32s3_spiflash.h:esp_rom_spiflash_common_cmd]`
- `[esp32s3_spiflash.h:esp_rom_spiflash_unlock]`
- `[esp32s3_spiflash.h:esp_rom_spiflash_lock]`
- `[esp32s3_spiflash.h:esp_rom_spiflash_config_param]`
- `[esp32s3_spiflash.h:esp_rom_spiflash_erase_chip]`
- `[esp32s3_spiflash.h:esp_rom_spiflash_erase_block]`
- `[esp32s3_spiflash.h:esp_rom_spiflash_erase_sector]`
- `[esp32s3_spiflash.h:esp_rom_spiflash_erase_area]`
- `[esp32s3_spiflash.h:esp_rom_spiflash_write]`
- `[esp32s3_spiflash.h:esp_rom_spiflash_read]`
- `[esp32s3_spiflash.h:esp_rom_spiflash_write_encrypted_enable]`
- `[esp32s3_spiflash.h:esp_rom_spiflash_prepare_encrypted_data]`
- `[esp32s3_spiflash.h:esp_rom_spiflash_write_encrypted_disable]`
- `[esp32s3_spiflash.h:esp_rom_spiflash_write_encrypted]`
- `[esp32s3_spiflash.h:esp_rom_spiflash_wait_idle]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
