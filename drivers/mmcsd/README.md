# MMC/SD/SDIO Drivers (`drivers/mmcsd`)

## Overview
Implements the MultiMediaCard (MMC), Secure Digital (SD) memory card, and SDIO bus/block driver stack over both native SDIO host controllers and SPI buses, along with CSD/ExtCSD parsing and `/proc/mmcsd` diagnostics.

## Interface
- `[mmcsd_sdio.c:mmcsd_slotinitialize]` - Initializes an MMC/SD block driver slot attached to a native `struct sdio_dev_s` host controller (`[mmcsd.h:struct mmcsd_state_s]`, `[mmcsd_sdio.h:struct mmcsd_csd_s]`).
- `[mmcsd_spi.c:mmcsd_spislotinitialize]` - Initializes an MMC/SD block driver slot over an SPI bus (`[mmcsd_spi.c:struct mmcsd_slot_s]`, `[mmcsd_spi.c:CONFIG_MMCSD_NSLOTS]`).
- `[sdio.c:sdio_probe]`, `[sdio.c:sdio_io_rw_direct]`, `[sdio.c:sdio_io_rw_extended]`, `[sdio.c:sdio_set_wide_bus]`, `[sdio.c:sdio_set_blocksize]`, `[sdio.c:sdio_enable_function]`, `[sdio.c:sdio_enable_interrupt]` - SDIO card enumeration and CMD52/CMD53 I/O helper API (`[sdio.c:struct sdio_cmd52]`, `[sdio.c:struct sdio_cmd53]`).
- `[mmcsd_procfs.c:mmcsd_initialize_procfs]` - Registers the `/proc/mmcsd` procfs entry when `[mmcsd.h:CONFIG_MMCSD_PROCFS]` is enabled.
- `[mmcsd_debug.c:mmcsd_dmpcsd]` - Decodes and logs 128-bit CSD register contents (`[mmcsd_debug.c:CONFIG_DEBUG_FS]`).

## Invariants
- Slot access and partition I/O share a per-slot mutex (`[mmcsd_sdio.c:nxmutex_lock]`, `[mmcsd_spi.c:nxmutex_lock]`) and open reference counts cannot exceed `[mmcsd_sdio.c:MAX_CREFS]`.
- Multi-block and DMA transfers respect `[mmcsd.h:CONFIG_SDIO_DMA]` and architecture preflight checks (`[mmcsd_sdio.c:CONFIG_ARCH_HAVE_SDIO_PREFLIGHT]`).

## Side Effects
- Registers and unregisters partition block device nodes (`/dev/mmcsd*`) via `[mmcsd_sdio.c:register_blockdriver]` and `[mmcsd_spi.c:register_blockdriver]`.
- Drives SDIO commands, bus clock/width changes, DMA setups, and SPI bus transactions (`[mmcsd_spi.c:SPI_SEND]`).

## Verification
- Run: `make test`
