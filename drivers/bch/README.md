# Block-to-Character (BCH) Drivers (`drivers/bch`)

## Overview
Provides the Block-to-Character (`bch`) translation library and VFS character driver wrapper that exposes a NuttX block device (`struct inode` with `block_operations`) as a byte-addressable character device with single-sector caching.

## Interface
- `bchdev_register.c:bchdev_register`, `bchdev_unregister.c:bchdev_unregister` - Registers and unregisters a character device node at `chardev` wrapping the block driver at `blkdev`.
- `bchdev_driver.c:g_bch_fops` - VFS character driver `file_operations` table implementing `open`, `close`, `read`, `write`, `seek`, `ioctl`, `poll`, and `unlink`.
- `bchlib_setup.c:bchlib_setup`, `bchlib_teardown.c:bchlib_teardown` - Allocates, initializes, and destroys a `bch.h:bchlib_s` context bound to a block driver inode.
- `bchlib_read.c:bchlib_read`, `bchlib_write.c:bchlib_write` - Performs byte-granularity reads and writes across sector boundaries using the internal sector cache.
- `bchlib_cache.c:bchlib_readsector`, `bchlib_cache.c:bchlib_flushsector` - Reads sectors into the single-sector cache buffer and flushes dirty cached sectors back to the underlying block device.
- `bch.h:bchlib_s`, `bch.h:MAX_OPENCNT` - Internal BCH state structure and maximum open reference count (`255`).

## Invariants
- `bchlib_teardown.c:bchlib_teardown` requires `bch->refs == 0`; attempting to tear down an active handle with open references returns `-EBUSY`.
- Opening a BCH character device requires `nxsched_capable(PR_CAP_RAWIO)` and enforces `bch->refs < MAX_OPENCNT` (`bchdev_driver.c:g_bch_fops`, `bch.h:MAX_OPENCNT`).
- If `bch->readonly` is true, `bchlib_write.c:bchlib_write` and write-mode `open` reject mutations with `-EACCES`.

## Side Effects
- Acquires `bch->lock` via `nxmutex_lock` around character driver operations (`bchdev_driver.c:g_bch_fops`).
- Allocates `bch.h:bchlib_s` and aligned sector buffers via `kmm_zalloc` and `kmm_malloc` (`bchlib_setup.c:bchlib_setup`, `bchlib_cache.c:bchlib_readsector`).
- Opens/closes the backing block driver (`open_blockdriver`, `close_blockdriver`), performs block device `read`, `write`, and `ioctl` operations, and registers/unregisters character nodes in the VFS (`bchdev_register.c:bchdev_register`, `bchdev_unregister.c:bchdev_unregister`).

## Verification
- Run: `make test`
