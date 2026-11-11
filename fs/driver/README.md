# Device Driver VFS Registration and Proxy Layer

## Overview
Manages the registration, lookup, opening, closing, unregistration, partitioning, merging, and proxy wrapping of character drivers, block drivers, MTD flash drivers, pipe drivers, and pseudo-directories in the NuttX pseudo-filesystem.

## Interface
- `fs_registerdriver.c:register_driver`, `fs_registerdriver.c:register_driver_with_size`, `fs_unregisterdriver.c:unregister_driver` - Character device driver registration and unregistration.
- `fs_registerblockdriver.c:register_blockdriver`, `fs_unregisterblockdriver.c:unregister_blockdriver`, `fs_findblockdriver.c:find_blockdriver`, `fs_openblockdriver.c:open_blockdriver`, `fs_closeblockdriver.c:close_blockdriver` - Block device driver lifecycle and lookup routines.
- `fs_registermtddriver.c:register_mtddriver`, `fs_unregistermtddriver.c:unregister_mtddriver`, `fs_findmtddriver.c:find_mtddriver`, `fs_closemtddriver.c:close_mtddriver` - MTD device driver lifecycle and lookup routines.
- `fs_registerpipedriver.c:register_pipedriver`, `fs_unregisterpipedriver.c:unregister_pipedriver`, `fs_registerpseudodir.c:register_pseudodir` - Pipe/FIFO driver and pseudo-directory registration.
- `fs_blockpartition.c:register_blockpartition`, `driver.h:register_partition_with_inode`, `fs_mtdpartition.c:register_mtdpartition`, `driver.h:register_partition_with_mtd`, `fs_blockmerge.c:register_merge_blockdriver` - Logical sub-partitioning and multi-partition linear merging for block and MTD devices.
- `driver.h:block_proxy`, `driver.h:mtd_proxy` - Temporary BCH character proxy over block devices and FTL block proxy over MTD devices.

## Invariants
- All inode reservations and removals (`inode_reserve`, `inode_remove`) must hold the global `inode_lock` semaphore (`fs_registerdriver.c:register_driver_with_size`, `fs_registerblockdriver.c:register_blockdriver`).
- Block partition reads and writes (`fs_blockpartition.c:part_read`, `fs_blockpartition.c:part_write`) clamp sector counts to `dev->nsectors` and offset by `dev->firstsector` so operations cannot escape partition bounds.
- Merged block devices require at least two partitions with identical `geo_sectorsize` (`fs_blockmerge.c:register_merge_blockdriver`, `fs_blockmerge.c:merge_open`).

## Side Effects
- Mutates the in-memory pseudo-filesystem inode tree and emits `notify_create`/`notify_mkdir`/`notify_unlink` events when `CONFIG_FS_NOTIFY` is enabled.
- Creates and unlinks temporary `/dev/tmpc*` and `/dev/tmpb*` proxy device nodes (`fs_blockproxy.c:block_proxy`, `fs_mtdproxy.c:mtd_proxy`).
- Invokes underlying block and MTD driver `.open`, `.close`, `.read`, `.write`, `.geometry`, and `.ioctl` callbacks.

## Verification
- Run: `make test`
