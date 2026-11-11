# 1-Wire Drivers (`drivers/1wire`)

## Overview
Provides the NuttX 1-Wire bus master infrastructure, ROM search and selection logic, CRC-8/CRC-16 validation helpers, and slave device drivers including DS2xxx family devices and the DS28E17 1-Wire-to-I2C master bridge.

## Interface
- `1wire.c:onewire_initialize`, `1wire.c:onewire_uninitialize` - Allocates and tears down a 1-Wire bus master instance (`1wire_internal.h:onewire_master_s`).
- `1wire.c:onewire_reset_resume`, `1wire.c:onewire_reset_select`, `1wire.c:onewire_readrom`, `1wire.c:onewire_triplet`, `1wire.c:onewire_search` - Performs 1-Wire bus reset, ROM selection, and binary tree ROM search.
- `1wire.c:onewire_addslave`, `1wire.c:onewire_removeslave`, `1wire.c:onewire_ioctl_setrom`, `1wire.c:onewire_ioctl_getfamilyroms` - Manages attached slave descriptors (`1wire_internal.h:onewire_slave_s`) and ROM filtering.
- `1wire_read.c:onewire_read`, `1wire_write.c:onewire_write`, `1wire_writeread.c:onewire_writeread` - Executes serialized read, write, and write-read transactions on a 1-Wire master.
- `1wire_crc.c:onewire_crc8`, `1wire_crc.c:onewire_crc16`, `1wire_crc.c:onewire_valid_rom`, `1wire_crc.c:onewire_check_crc16` - Computes 1-Wire CRC-8 and CRC-16 checksums and validates 64-bit ROM codes.
- `1wire_ds2xxx.c:ds2xxx_initialize`, `1wire_ds2xxx.c:ds2xxx_dev_s` - Registers character drivers for DS2xxx 1-Wire slave devices.
- `ds28e17.c:ds28e17_initialize`, `ds28e17.c:ds28e17_lower_half`, `ds28e17.c:ds28e17_lower_half_unregister`, `ds28e17.c:ds28e17_search` - Exposes DS28E17 1-Wire-to-I2C bridge instances as NuttX I2C master lower halves.

## Invariants
- `1wire.c:onewire_initialize` requires a non-null lower-half `dev` pointer and `maxslaves > 0`.
- `1wire.c:onewire_search` asserts `master->insearch == false` to prevent re-entrant ROM discovery on the same bus (`1wire_internal.h:onewire_master_s`).
- `1wire.c:onewire_addslave` and `1wire.c:onewire_removeslave` require valid `master` and `slave` pointers and enforce `master->nslaves <= master->maxslaves`.
- All bus transactions must hold the recursive bus lock `master->devlock` (`1wire_internal.h:onewire_master_s`).

## Side Effects
- Acquires recursive mutexes via `nxrmutex_lock` (`1wire.c:onewire_search`, `1wire_read.c:onewire_read`, `1wire_write.c:onewire_write`, `1wire_writeread.c:onewire_writeread`, `ds28e17.c:ds28e17_lower_half`).
- Performs hardware 1-Wire bus signaling (`ONEWIRE_RESET`, `ONEWIRE_WRITE`, `ONEWIRE_READ`, `ONEWIRE_WRITEBIT`, `ONEWIRE_READBIT`) and registers character devices via `register_driver` (`1wire_ds2xxx.c:ds2xxx_initialize`).
- Allocates master and device state on the kernel heap via `kmm_malloc` and `kmm_zalloc` (`1wire.c:onewire_initialize`, `1wire_ds2xxx.c:ds2xxx_initialize`, `ds28e17.c:ds28e17_initialize`).

## Verification
- Run: `make test`
