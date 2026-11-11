# High Memory (ESP Himem) Subsystem Headers (`include/nuttx/himem`)

## Overview
Defines the character driver `ioctl` commands, block/range handle types, and initialization entry point for banking and mapping external SPI RAM above the directly addressable window on ESP32 and ESP32-S3 targets (`CONFIG_ESP32_SPIRAM` / `CONFIG_ESP32S3_SPIRAM`).

## Interface
- `himem.h:ESP_HIMEM_BLKSZ` - Bank switching block size (`0x10000` on ESP32-S3, `0x8000` on ESP32).
- `himem.h:HIMEMIOC_ALLOC_BLOCKS`, `himem.h:HIMEMIOC_FREE_BLOCKS`, `himem.h:HIMEMIOC_ALLOC_MAP_RANGE`, `himem.h:HIMEMIOC_FREE_MAP_RANGE`, `himem.h:HIMEMIOC_MAP`, `himem.h:HIMEMIOC_UNMAP`, `himem.h:HIMEMIOC_GET_PHYS_SIZE`, `himem.h:HIMEMIOC_GET_FREE_SIZE` - Himem character device `ioctl` command codes.
- `himem.h:esp_himem_rangedata_t`, `himem.h:esp_himem_ramdata_t`, `himem.h:esp_himem_handle_t`, `himem.h:esp_himem_rangehandle_t`, `himem.h:esp_himem_par` - Physical RAM block handles, virtual address range handles, and `ioctl` request parameter structure.
- `himem.h:esp_himem_init` - Initializes the ESP Himem allocator and registers its character device.

## Invariants
- All physical RAM offsets (`ram_offset`), virtual range offsets (`range_offset`), and mapping lengths (`len`) in `himem.h:esp_himem_par` must be aligned to `himem.h:ESP_HIMEM_BLKSZ`.

## Side Effects
- `himem.h:esp_himem_init` initializes the external PSRAM bank metadata and registers the Himem character driver.
- `HIMEMIOC_MAP` and `HIMEMIOC_UNMAP` reprogram MMU cache flash/PSRAM page tables to map physical PSRAM blocks into the CPU virtual address space.

## Verification
- Run: `make test`
