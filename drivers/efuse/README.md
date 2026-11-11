# eFuse Character Driver (`drivers/efuse`)

## Overview
Implements the upper-half character driver for non-volatile One-Time Programmable (OTP) eFuse memory controllers, bridging VFS `ioctl` requests (`EFUSEIOC_READ_FIELD`, `EFUSEIOC_WRITE_FIELD`) to an architecture-specific `efuse_lowerhalf_s` implementation.

## Interface
- `efuse.c:efuse_register`, `efuse.c:efuse_unregister` - Registers and unregisters an eFuse character device at `path` backed by `lower`.
- `efuse.c:efuse_upperhalf_s` - Upper-half driver state holding the mutual exclusion lock (`lock`), device path, and `efuse_lowerhalf_s` pointer.

## Invariants
- `efuse.c:efuse_register` asserts `path != NULL && lower != NULL`.
- `efuse_ioctl` asserts `upper != NULL && lower != NULL`, `lower->ops->read_field != NULL` for `EFUSEIOC_READ_FIELD`, and `lower->ops->write_field != NULL` for `EFUSEIOC_WRITE_FIELD` (`efuse.c:efuse_register`).

## Side Effects
- Acquires `upper->lock` via `nxmutex_lock` around `ioctl` operations (`efuse.c:efuse_register`).
- Registers and unregisters VFS character drivers via `register_driver` and `unregister_driver`, and allocates/frees `efuse.c:efuse_upperhalf_s` via `kmm_zalloc`/`kmm_free` (`efuse.c:efuse_register`, `efuse.c:efuse_unregister`).
- Invokes lower-half `read_field`, `write_field`, and `ioctl` operations that read or permanently blow hardware eFuse bits (`efuse.c:efuse_register`).

## Verification
- Run: `make test`
