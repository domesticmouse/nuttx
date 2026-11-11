# SPI Bus Drivers and Helpers (`drivers/spi`)

## Overview
Provides the upper-half SPI master character driver (`spi_driver.c`), SPI slave character driver (`spi_slave_driver.c`), multi-message transaction sequencer (`spi_transfer.c`), GPIO bit-bang SPI master engine (`spi_bitbang.c`), Lattice iCE40 FPGA SPI configuration driver (`ice40.c`), and simulated SPI/QSPI NOR flash devices (`spi_flash.c`, `qspi_flash.c`).

## Interface
- `[spi_driver.c:spi_register]` - Registers an upper-half SPI master character device (`/dev/spiN`) wrapping a `struct spi_dev_s` bus instance.
- `[spi_slave_driver.c:spi_slave_register]` - Registers an upper-half SPI slave controller character device (`/dev/spislvN`) wrapping a `struct spi_slave_ctrlr_s`.
- `[spi_transfer.c:spi_transfer]`, `[spi_transfer.c:spi_transferseqs]` - Executes one or more `spi_sequence_s` transaction sequences on an SPI bus with chip-select assertion, frequency/mode/nbits reconfiguration, and inter-transaction delays.
- `[spi_bitbang.c:spi_create_bitbang]`, `[spi_bitbang.c:spi_destroy_bitbang]` - Allocates and destroys a bit-banged SPI master bus instance (`struct spi_dev_s`) using lower-half bit-bang operations (`struct spi_bitbang_ops_s`).
- `[ice40.c:ice40_register]` - Registers a Lattice iCE40 FPGA bitstream programming character device over SPI.
- `[spi_flash.c:spi_flash_initialize]`, `[spi_flash.c:g_spidev_m25p]`, `[spi_flash.c:g_spidev_sst26]`, `[spi_flash.c:g_spidev_w25]`, `[spi_flash.c:g_spidev_custom]` - Initializes an emulated SPI NOR flash device for testing MTD drivers.
- `[qspi_flash.c:qspi_flash_initialize]`, `[qspi_flash.c:qspi_flash_memory]`, `[qspi_flash.c:g_qspidev]` - Initializes an emulated Quad-SPI flash device and returns its backing memory buffer.

## Invariants
- `[spi_transfer.c:spi_transfer]` asserts `DEBUGASSERT(spi != NULL && seq != NULL && seq->trans != NULL)` and `[spi_transfer.c:spi_transferseqs]` asserts `DEBUGASSERT(spi != NULL && seqs != NULL && nseqs > 0)`.
- `[spi_bitbang.c:spi_create_bitbang]` asserts that the lower-half operations `select`, `setfrequency`, `setmode`, and `exchange` are non-null.
- `[spi_driver.c:spi_register]` and `[spi_slave_driver.c:spi_slave_register]` assert `DEBUGASSERT(priv->crefs > 0)` on close and require valid `filep->f_inode->i_private`.
- `[qspi_flash.c:qspi_flash_initialize]` command handlers assert `DEBUGASSERT(cmdinfo->cmd < 256)` and `DEBUGASSERT(cmdinfo->buffer != NULL && cmdinfo->buflen > 0)` when data transfer is requested.

## Side Effects
- `[spi_driver.c:spi_register]`, `[spi_slave_driver.c:spi_slave_register]`, and `[ice40.c:ice40_register]` register character drivers in the VFS via `register_driver`.
- `[spi_transfer.c:spi_transfer]` acquires exclusive bus access via `SPI_LOCK(spi, true)`, mutates bus frequency/mode/word-width, toggles chip-select lines (`SPI_SELECT`), and performs hardware SPI transfers (`SPI_EXCHANGE` / `SPI_SNDBLOCK` / `SPI_RECVBLOCK`).
- `[spi_bitbang.c:spi_create_bitbang]` allocates driver state via `kmm_zalloc` and drives GPIO clock/MOSI/MISO/CS pins under `nxmutex_lock`.

## Verification
- Run: `make test`
