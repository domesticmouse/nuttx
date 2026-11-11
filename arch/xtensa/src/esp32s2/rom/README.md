# rom (`nuttx/arch/xtensa/src/esp32s2/rom`)

## Overview
Hardware abstraction and architecture package for `rom` under `nuttx/arch/xtensa/src/esp32s2/rom`, providing 3 header file(s) and 0 source file(s) (including `esp32s2_libc_stubs.h`, `esp32s2_opi_flash.h`, `esp32s2_spiflash.h`).

## Interface
- `[esp32s2_libc_stubs.h:esp_setup_syscall_table]`
- `[esp32s2_libc_stubs.h:syscall_stub_table]`
- `[esp32s2_libc_stubs.h:_lock_t]`
- `[esp32s2_opi_flash.h:esp_rom_spi_cmd_config]`
- `[esp32s2_opi_flash.h:esp_rom_spi_cmd_start]`
- `[esp32s2_opi_flash.h:esp_rom_opiflash_pin_config]`
- `[esp32s2_opi_flash.h:esp_rom_spi_set_op_mode]`
- `[esp32s2_opi_flash.h:esp_rom_spi_set_dtr_swap_mode]`
- `[esp32s2_opi_flash.h:esp_rom_opiflash_mode_reset]`
- `[esp32s2_opi_flash.h:esp_rom_opiflash_exec_cmd]`
- `[esp32s2_opi_flash.h:esp_rom_opiflash_soft_reset]`
- `[esp32s2_opi_flash.h:esp_rom_opiflash_read_id]`
- `[esp32s2_opi_flash.h:esp_rom_opiflash_rdsr]`
- `[esp32s2_opi_flash.h:esp_rom_opiflash_wait_idle]`
- `[esp32s2_opi_flash.h:esp_rom_opiflash_rdcr2]`
- `[esp32s2_opi_flash.h:esp_rom_opiflash_wrcr2]`
- `[esp32s2_opi_flash.h:esp_rom_opiflash_erase_sector]`
- `[esp32s2_opi_flash.h:esp_rom_opiflash_erase_block_64k]`
- `[esp32s2_opi_flash.h:esp_rom_opiflash_erase_area]`
- `[esp32s2_opi_flash.h:esp_rom_opiflash_read]`
- `[esp32s2_opi_flash.h:esp_rom_opiflash_write]`
- `[esp32s2_opi_flash.h:esp_rom_opiflash_set_mode]`
- `[esp32s2_opi_flash.h:esp_rom_spi_cmd_t]`
- `[esp32s2_opi_flash.h:ESP_ROM_OPIFLASH_MUX_TAKE]`
- `[esp32s2_opi_flash.h:ESP_ROM_OPIFLASH_MUX_GIVE]`
- `[esp32s2_opi_flash.h:ESP_ROM_OPIFLASH_SEL_CS0]`
- `[esp32s2_opi_flash.h:ESP_ROM_OPIFLASH_SEL_CS1]`
- `[esp32s2_opi_flash.h:ESP_ROM_SPIFLASH_BUSY_FLAG]`
- `[esp32s2_opi_flash.h:ESP_ROM_SPIFLASH_WRENABLE_FLAG]`
- `[esp32s2_opi_flash.h:ESP_ROM_SPIFLASH_BP0]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
