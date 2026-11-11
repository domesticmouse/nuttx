# rom (`nuttx/arch/risc-v/src/esp32c3-legacy/rom`)

## Overview
Hardware abstraction and architecture package for `rom` under `nuttx/arch/risc-v/src/esp32c3-legacy/rom`, providing 2 header file(s) and 0 source file(s) (including `esp32c3_libc_stubs.h`, `esp32c3_spiflash.h`).

## Interface
- `[esp32c3_libc_stubs.h:setup_syscall_table]`
- `[esp32c3_libc_stubs.h:syscall_stub_table]`
- `[esp32c3_libc_stubs.h:_lock_t]`
- `[esp32c3_spiflash.h:esp_rom_spiflash_fix_dummylen]`
- `[esp32c3_spiflash.h:esp_rom_spiflash_select_qiomode]`
- `[esp32c3_spiflash.h:esp_rom_spiflash_set_drvs]`
- `[esp32c3_spiflash.h:esp_rom_spiflash_select_padsfunc]`
- `[esp32c3_spiflash.h:esp_rom_spiflash_attach]`
- `[esp32c3_spiflash.h:esp_rom_spiflash_read_status]`
- `[esp32c3_spiflash.h:esp32c3_spiflash_read_statushigh]`
- `[esp32c3_spiflash.h:esp32c3_spiflash_write_status]`
- `[esp32c3_spiflash.h:esp_rom_spiflash_read_user_cmd]`
- `[esp32c3_spiflash.h:esp_rom_spiflash_config_readmode]`
- `[esp32c3_spiflash.h:esp_rom_spiflash_config_clk]`
- `[esp32c3_spiflash.h:esp_rom_spiflash_common_cmd]`
- `[esp32c3_spiflash.h:esp_rom_spiflash_unlock]`
- `[esp32c3_spiflash.h:esp_rom_spiflash_lock]`
- `[esp32c3_spiflash.h:esp_rom_spiflash_config_param]`
- `[esp32c3_spiflash.h:esp_rom_spiflash_erase_chip]`
- `[esp32c3_spiflash.h:esp_rom_spiflash_erase_block]`
- `[esp32c3_spiflash.h:esp_rom_spiflash_erase_sector]`
- `[esp32c3_spiflash.h:esp_rom_spiflash_erase_area]`
- `[esp32c3_spiflash.h:esp_rom_spiflash_write]`
- `[esp32c3_spiflash.h:esp_rom_spiflash_read]`
- `[esp32c3_spiflash.h:esp_rom_spiflash_write_encrypted_enable]`
- `[esp32c3_spiflash.h:esp_rom_spiflash_prepare_encrypted_data]`
- `[esp32c3_spiflash.h:esp_rom_spiflash_write_encrypted_disable]`
- `[esp32c3_spiflash.h:esp_rom_spiflash_write_encrypted]`
- `[esp32c3_spiflash.h:esp_rom_spiflash_wait_idle]`
- `[esp32c3_spiflash.h:esp_rom_spiflash_select_qio_pins]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
