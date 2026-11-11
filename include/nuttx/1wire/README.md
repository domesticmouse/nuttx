# 1-Wire Subsystem Headers (`include/nuttx/1wire`)

## Overview
Defines the upper-half and lower-half driver interfaces, master bus abstractions, ROM command constants, CRC helpers, and device-specific initialization APIs for the NuttX 1-Wire (`1wire`) subsystem, including DS2xxx EEPROMs and the DS28E17 1-Wire-to-I2C master bridge.

## Interface
- `1wire.h:onewire_ops_s`, `1wire.h:onewire_dev_s`, `1wire.h:onewire_availroms_s` - Lower-half 1-Wire bus operation vtable, device handle, and ROM discovery buffer structures.
- `1wire.h:ONEWIRE_RESET`, `1wire.h:ONEWIRE_WRITE`, `1wire.h:ONEWIRE_READ`, `1wire.h:ONEWIRE_EXCHANGE`, `1wire.h:ONEWIRE_WRITEBIT`, `1wire.h:ONEWIRE_READBIT` - Dispatch macros invoking lower-half `onewire_ops_s` methods.
- `1wire.h:ONEWIREIOC_SETROM`, `1wire.h:ONEWIREIOC_GETFAMILYROMS`, `1wire.h:ONEWIRE_CMD_SEARCH`, `1wire.h:ONEWIRE_CMD_MATCH_ROM`, `1wire.h:ONEWIRE_CMD_SKIP_ROM` - 1-Wire `ioctl` commands and standard ROM command opcodes.
- `1wire_crc.h:onewire_crc8`, `1wire_crc.h:onewire_crc16`, `1wire_crc.h:onewire_valid_rom`, `1wire_crc.h:onewire_check_crc16` - 8-bit/16-bit 1-Wire CRC calculation and ROM validation functions.
- `1wire_master.h:onewire_master_s`, `1wire_master.h:onewire_config_s`, `1wire_master.h:onewire_initialize`, `1wire_master.h:onewire_uninitialize`, `1wire_master.h:onewire_write`, `1wire_master.h:onewire_read`, `1wire_master.h:onewire_writeread`, `1wire_master.h:onewire_search`, `1wire_master.h:onewire_isalarm` - Upper-half 1-Wire master bus management, slave ROM search, and transfer APIs.
- `1wire_ds2xxx.h:ds2xxx_eeproms_e`, `1wire_ds2xxx.h:ds2xxx_initialize` - Device enumeration and initialization entry point for DS243x/DS28Exx 1-Wire EEPROMs.
- `ds28e17.h:ds28e17_dev_s`, `ds28e17.h:ds28e17_initialize`, `ds28e17.h:ds28e17_search`, `ds28e17.h:ds28e17_lower_half`, `ds28e17.h:ds28e17_lower_half_unregister` - Initialization and virtual I2C master lower-half management for the DS28E17 1-Wire-to-I2C bridge.

## Invariants
- `1wire.h:onewire_dev_s` must have a valid, non-null `ops` pointer (`1wire.h:onewire_ops_s`) before invoking `ONEWIRE_RESET`, `ONEWIRE_WRITE`, `ONEWIRE_READ`, `ONEWIRE_EXCHANGE`, `ONEWIRE_WRITEBIT`, or `ONEWIRE_READBIT`.
- `1wire_crc.h:onewire_valid_rom` requires the 64-bit ROM code to carry a valid 8-bit CRC in its most significant byte.
- `ds28e17.h:DS_DEFAULT_MAXSLAVES` bounds default slave discovery capacity unless overridden.

## Side Effects
- Invoking `1wire.h:onewire_ops_s` callbacks (`reset`, `write`, `read`, `exchange`, `writebit`, `readbit`) or `1wire_master.h:onewire_search` performs physical single-wire bus signaling and mutates bus/slave state.
- `1wire_ds2xxx.h:ds2xxx_initialize` and `ds28e17.h:ds28e17_initialize` allocate driver state and register device nodes or virtual I2C master instances.

## Verification
- Run: `make test`
