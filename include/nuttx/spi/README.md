# NuttX SPI & QSPI Subsystem (`include/nuttx/spi`)

## Overview
Defines the Serial Peripheral Interface (`SPI`) master (`spi.h`), SPI slave controller/device (`slave.h`), Quad/Octal SPI (`qspi.h`), sequenced transaction helper (`spi_transfer.h`), GPIO bit-bang SPI (`spi_bitbang.h`, `spi_bitbang.c`), Lattice iCE40 FPGA SPI programmer (`ice40.h`), and simulated SPI/QSPI flash (`spi_flash.h`, `qspi_flash.h`) interfaces.

## Interface
- `spi.h:spi_dev_s`, `spi.h:spi_ops_s`, `spi.h:spi_mode_e`, `spi.h:spi_devtype_e`, `spi.h:spi_hwfeatures_t`, `spi.h:SPI_LOCK`, `spi.h:SPI_SELECT`, `spi.h:SPI_SETFREQUENCY`, `spi.h:SPI_SETMODE`, `spi.h:SPI_SETBITS`, `spi.h:SPI_SEND`, `spi.h:SPI_EXCHANGE`, `spi.h:SPI_SNDBLOCK`, `spi.h:SPI_RECVBLOCK`, `spi.h:SPIDEV_ID` - Core SPI master vtable, dispatch macros, clocking modes (`SPIDEV_MODE0`..`SPIDEV_MODETI`), and composite device IDs.
- `spi_transfer.h:spi_trans_s`, `spi_transfer.h:spi_sequence_s`, `spi_transfer.h:spi_transfer`, `spi_transfer.h:spi_transferseqs`, `spi_transfer.h:spi_register`, `spi_transfer.h:SPIIOC_TRANSFER` - Multi-segment SPI transaction sequencer and `/dev/spiN` character driver interface.
- `slave.h:spi_slave_ctrlr_s`, `slave.h:spi_slave_ctrlrops_s`, `slave.h:spi_slave_dev_s`, `slave.h:spi_slave_devops_s`, `slave.h:spi_slave_register`, `slave.h:SPIS_CTRLR_BIND`, `slave.h:SPIS_CTRLR_ENQUEUE` - SPI slave controller and peripheral device abstraction.
- `qspi.h:qspi_dev_s`, `qspi.h:qspi_ops_s`, `qspi.h:qspi_cmdinfo_s`, `qspi.h:qspi_meminfo_s`, `qspi.h:QSPI_LOCK`, `qspi.h:QSPI_COMMAND`, `qspi.h:QSPI_MEMORY`, `qspi.h:QSPI_ALLOC`, `qspi.h:QSPI_FREE` - Quad-SPI command and memory-mapped transfer interfaces.
- `spi_bitbang.h:spi_bitbang_s`, `spi_bitbang.h:spi_bitbang_ops_s`, `spi_bitbang.h:spi_create_bitbang`, `spi_bitbang.h:spi_destroy_bitbang`, `spi_bitbang.c:spi_exchange` - Software bit-bang SPI master skeleton and included template implementation.
- `ice40.h:ice40_dev_s`, `ice40.h:ice40_ops_s`, `ice40.h:ice40_register`, `ice40.h:FPGAIOC_WRITE` - Lattice iCE40 FPGA bitstream configuration over SPI.
- `spi_flash.h:spi_flash_initialize`, `qspi_flash.h:qspi_flash_initialize` - Simulated SPI/QSPI NOR flash initialization.

## Invariants
- Callers sharing an SPI or QSPI bus must acquire exclusive access via `spi.h:SPI_LOCK(dev, true)` (or `qspi.h:QSPI_LOCK(dev, true)`) before asserting chip select with `spi.h:SPI_SELECT`, and must re-apply `SPI_SETFREQUENCY`, `SPI_SETBITS`, and `SPI_SETMODE` after locking because another client may have reconfigured the bus.
- When `nbits <= 8` in `spi.h:SPI_SETBITS`, buffers passed to `spi.h:SPI_EXCHANGE`, `spi.h:SPI_SNDBLOCK`, and `spi.h:SPI_RECVBLOCK` are packed as `uint8_t`; when `nbits > 8`, buffers are packed as `uint16_t` (with `nwords` counting words, not bytes).

## Side Effects
- `spi.h:SPI_SELECT`, `spi.h:SPI_SEND`, `spi.h:SPI_EXCHANGE`, and `qspi.h:QSPI_MEMORY` toggle physical chip-select GPIOs and trigger synchronous or DMA-backed SPI bus transfers.
- `spi_transfer.h:spi_register` and `slave.h:spi_slave_register` register `/dev/spi*` and `/dev/spislv*` character device nodes in the VFS.

## Verification
- Run: `make test`
