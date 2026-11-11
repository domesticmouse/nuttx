# EEPROM Device Driver Headers (`include/nuttx/eeprom`)

## Overview
Defines the character and MTD-backed driver interfaces, geometry structures, `ioctl` commands, and part enumerations for I2C (AT24xx / M24xx) and SPI (AT25xx / M95xx) Electrically Erasable Programmable Read-Only Memory (EEPROM) devices.

## Interface
- `eeprom.h:EEPIOC_GEOMETRY`, `eeprom.h:EEPIOC_SETSPEED`, `eeprom.h:EEPIOC_PAGEERASE`, `eeprom.h:EEPIOC_SECTORERASE`, `eeprom.h:EEPIOC_CHIPERASE`, `eeprom.h:EEPIOC_BLOCKPROTECT` - EEPROM `ioctl` control commands.
- `eeprom.h:eeprom_geometry_s`, `eeprom.h:eeprom_dev_s` - EEPROM device geometry descriptor (`npages`, `sectsize`, `pagesize`) and lower-half read/write/ioctl method structure.
- `eeprom.h:eeprom_24xx_e`, `eeprom.h:eeprom_25xx_e` - Part number enumerations for 24xx I2C EEPROMs and 25xx SPI EEPROMs.
- `eeprom.h:ee24xx_initialize`, `eeprom.h:ee25xx_initialize`, `eeprom.h:ee25xx_initialize_as_eeprom_dev`, `eeprom.h:ee25xx_teardown` - I2C and SPI EEPROM driver initialization and teardown functions.

## Invariants
- `eeprom.h:ee24xx_initialize` and `eeprom.h:ee25xx_initialize` require a valid `i2c_master_s` or `spi_dev_s` bus instance and a supported `eeprom_24xx_e` / `eeprom_25xx_e` device type.
- When initialized with `readonly != 0`, write and erase operations on the resulting EEPROM device are rejected.

## Side Effects
- `eeprom.h:ee24xx_initialize` and `eeprom.h:ee25xx_initialize` allocate driver structures and register a character device at `devname` in the VFS.
- `eeprom.h:eeprom_dev_s` operations perform page-aligned I2C/SPI bus transactions and non-volatile memory write/erase cycles.

## Verification
- Run: `make test`
