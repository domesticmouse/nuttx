# Core Device Drivers & Block Caching Headers (`include/nuttx/drivers`)

## Overview
Declares system-wide pseudo-device and core driver initialization routines (`/dev/null`, `/dev/zero`, `/dev/random`, `/dev/urandom`, `/dev/crypto`, `/dev/mem`), block-to-character (`bch`) wrappers, RAM/ROM disks, read-ahead/write-back block buffer caching (`rwbuffer`), simple static address environment mappings, OP-TEE drivers, Goldfish pipe drivers, and RPMSG remote block/character device bridges.

## Interface
- `drivers.h:drivers_early_initialize`, `drivers.h:drivers_initialize`, `drivers.h:devnull_register`, `drivers.h:devzero_register`, `drivers.h:devrandom_register`, `drivers.h:devurandom_register`, `drivers.h:devcrypto_register`, `drivers.h:devmem_register`, `drivers.h:devascii_register` - System driver initialization and standard pseudo-device registration functions.
- `drivers.h:bchdev_register`, `drivers.h:bchdev_unregister`, `drivers.h:bchlib_setup`, `drivers.h:bchlib_teardown`, `drivers.h:bchlib_read`, `drivers.h:bchlib_write` - Block-to-Character (`bch`) device wrapper and library APIs.
- `ramdisk.h:ramdisk_register`, `ramdisk.h:romdisk_register`, `ramdisk.h:mkrd`, `ramdisk.h:RDFLAG_WRENABLED`, `ramdisk.h:RDFLAG_FUNLINK` - RAM disk and ROM disk block device registration.
- `rwbuffer.h:rwbuffer_s`, `rwbuffer.h:rwb_initialize`, `rwbuffer.h:rwb_uninitialize`, `rwbuffer.h:rwb_read`, `rwbuffer.h:rwb_write`, `rwbuffer.h:rwb_readbytes`, `rwbuffer.h:rwb_mediaremoved`, `rwbuffer.h:rwb_invalidate`, `rwbuffer.h:rwb_flush`, `rwbuffer.h:rwb_discard` - Block device write-buffering and read-ahead caching layer.
- `addrenv.h:simple_addrenv_s`, `addrenv.h:simple_addrenv_initialize` - Static virtual-to-physical address translation table initialization.
- `goldfish_pipe.h:goldfish_pipe_register`, `optee.h:optee_register` - Android Goldfish emulator pipe driver and ARM OP-TEE driver registration.
- `rpmsgblk.h:rpmsgblk_server_init`, `rpmsgblk.h:rpmsgblk_register`, `rpmsgdev.h:rpmsgdev_server_init`, `rpmsgdev.h:rpmsgdev_export`, `rpmsgdev.h:rpmsgdev_export_with_prefix`, `rpmsgdev.h:rpmsgdev_register` - Cross-core RPMSG remote block and character device proxy APIs.

## Invariants
- `rwbuffer.h:rwbuffer_s` requires `blocksize > 0`, `nblocks > 0`, and valid `wrflush` / `rhreload` callbacks before calling `rwb_initialize`.
- `drivers.h:bchlib_setup` returns an opaque handle that must be released via `bchlib_teardown` only after all concurrent `bchlib_read`/`bchlib_write` calls complete.

## Side Effects
- Registration routines (`devnull_register`, `bchdev_register`, `ramdisk_register`, `rpmsgdev_register`, `rpmsgblk_register`, `optee_register`, `goldfish_pipe_register`) create VFS character or block device nodes and allocate kernel state.
- `rwbuffer.h:rwb_initialize` allocates cache buffers and schedules delayed flush work (`struct work_s`) on the system work queue when `CONFIG_DRVR_WRITEBUFFER` is enabled.

## Verification
- Run: `make test`
