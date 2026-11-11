# EEPROM Character Drivers (`drivers/eeprom`)

## Overview
Provides byte-addressable VFS character drivers for serial EEPROM memory devices over I2C (`24xx` series, AT24CSxx) and SPI (`25xx` series, AT25xx, M95xxx), handling page-aligned write segmentation and write-complete polling.

## Interface
- `i2c_xx24xx.c:ee24xx_initialize`, `i2c_xx24xx.c:ee24xx_dev_s`, `i2c_xx24xx.c:ee24xx_geom_s` - Initializes and registers an I2C 24xx-series EEPROM character driver at `devname`.
- `spi_xx25xx.c:ee25xx_initialize`, `spi_xx25xx.c:ee25xx_initialize_as_eeprom_dev`, `spi_xx25xx.c:ee25xx_teardown`, `spi_xx25xx.c:ee25xx_dev_s`, `spi_xx25xx.c:ee25xx_geom_s` - Initializes, exposes as an `eeprom_dev_s`, or tears down an SPI 25xx-series EEPROM character driver.

## Invariants
- `i2c_xx24xx.c:ee24xx_initialize` and `spi_xx25xx.c:ee25xx_initialize` assert `eedev != NULL` and `eedev->pgsize > 0` (and `eedev->secsize > 0` for SPI EEPROMs).
- File operations assert `inode->i_private != NULL` (`i2c_xx24xx.c:ee24xx_initialize`, `spi_xx25xx.c:ee25xx_initialize`).
- Read-only instances (`eedev->readonly`) reject `write` calls with `-EACCES`.

## Side Effects
- Acquires `eedev->lock` via `nxmutex_lock` to serialize multi-page read, write, and `ioctl` operations (`i2c_xx24xx.c:ee24xx_initialize`, `spi_xx25xx.c:ee25xx_initialize`).
- Performs I2C (`I2C_TRANSFER` in `i2c_xx24xx.c:ee24xx_initialize`) and SPI (`SPI_LOCK`, `SPI_SELECT`, `SPI_SEND`, `SPI_EXCHANGE`, `SPI_SNDBLOCK`, `SPI_RECVBLOCK` in `spi_xx25xx.c:ee25xx_initialize`) bus transactions.
- Registers character devices via `register_driver` and allocates device contexts and page write buffers via `kmm_zalloc` and `kmm_malloc` (`i2c_xx24xx.c:ee24xx_initialize`, `spi_xx25xx.c:ee25xx_initialize`).

## Verification
- Run: `make test`
