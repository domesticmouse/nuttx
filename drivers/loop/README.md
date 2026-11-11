# Loop Device Driver (`drivers/loop`)

## Overview
Provides the loop control character device (`/dev/loop`) and block device wrapper (`losetup`/`loteardown`) that expose regular files or character devices as sector-addressable block devices in NuttX.

## Interface
- `[loop.c:loop_register]` - Registers the `/dev/loop` control character driver (`[loop.c:CONFIG_DEV_LOOP]`) handling `LOOPIOC_SETUP` and `LOOPIOC_TEARDOWN` ioctls.
- `[losetup.c:losetup]` - Binds a backing file or character device at a given sector size and byte offset to a newly registered block device node (`[losetup.c:struct loop_struct_s]`).
- `[losetup.c:loteardown]` - Unregisters a loop block device and closes the underlying backing file (`[losetup.c:g_bops]`).

## Invariants
- Open reference count `[losetup.c:opencnt]` must not exceed `[losetup.c:MAX_OPENCNT]` (255), and `[losetup.c:loteardown]` fails with `-EBUSY` if `opencnt > 0`.
- All sector read/write operations on a loop device are serialized via `[losetup.c:lock]` (`nxmutex_lock` / `nxmutex_unlock`).

## Side Effects
- Registers and unregisters VFS character and block drivers (`[loop.c:register_driver]`, `[losetup.c:register_blockdriver]`, `unregister_blockdriver`).
- Opens, seeks, reads, and writes the underlying backing VFS file (`[losetup.c:devfile]`) via `file_open`, `file_seek`, `file_read`, and `file_write`.

## Verification
- Run: `make test`
