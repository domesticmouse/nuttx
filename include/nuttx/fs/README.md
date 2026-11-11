# Virtual File System (VFS) & Filesystem Headers (`include/nuttx/fs`)

## Overview
Defines the core NuttX Virtual File System (VFS) data structures (`file`, `inode`, `file_operations`, `mountpt_operations`), global `ioctl` command namespaces, scatter/gather `uio` helpers, partition table parsers, automounter, loopback block/MTD devices, and filesystem-specific interfaces (FAT, HostFS, NFS, NXFFS, ProcFS, SmartFS, UserFS, XIPFS).

## Interface
- `fs.h:file_operations`, `fs.h:block_operations`, `fs.h:mountpt_operations`, `fs.h:inode`, `fs.h:file`, `fs.h:fs_dirent_s` - Core VFS operation tables, inode node flags (`INODE_IS_DRIVER`, `INODE_IS_BLOCK`, `INODE_IS_MOUNTPT`, etc.), and open file descriptors.
- `fs.h:register_driver`, `fs.h:register_blockdriver`, `fs.h:unregister_driver`, `fs.h:unregister_blockdriver`, `fs.h:nx_mount`, `fs.h:nx_umount2`, `fs.h:file_open`, `fs.h:file_close`, `fs.h:file_read`, `fs.h:file_write`, `fs.h:file_seek`, `fs.h:file_ioctl`, `fs.h:file_poll`, `fs.h:file_mmap` - Kernel VFS driver registration, mount management, and internal `struct file` I/O operations.
- `ioctl.h:_IOC`, `ioctl.h:_IOC_TYPE`, `ioctl.h:_IOC_NR`, `ioctl.h:geometry`, `ioctl.h:partition_info_s`, `ioctl.h:pipe_peek_s` - Master `ioctl` type base constants (`_TIOCBASE`, `_FIOCBASE`, `_BIOCBASE`, `_MTDIOCBASE`, etc.) and common block/pipe `ioctl` structures.
- `automount.h:automount_lower_s`, `automount.h:automount_initialize`, `automount.h:automount_uninitialize` - Block media insertion/removal automounter interface.
- `loop.h:losetup_s`, `loop.h:loop_register`, `loop.h:losetup`, `loop.h:loteardown`, `loopmtd.h:mtd_losetup_s`, `loopmtd.h:mtd_loop_register` - File-backed block and MTD loopback device interfaces.
- `partition.h:partition_s`, `partition.h:parse_block_partition`, `partition.h:parse_mtd_partition` - Block and MTD partition table parsing callbacks and entry points.
- `procfs.h:procfs_operations`, `procfs.h:procfs_entry_s`, `procfs.h:procfs_meminfo_entry_s`, `procfs.h:procfs_register`, `procfs.h:procfs_register_meminfo`, `procfs.h:procfs_memcpy`, `procfs.h:procfs_snprintf` - `/proc` filesystem entry and heap memory info registration APIs.
- `uio.h:uio`, `uio.h:uio_init`, `uio.h:uio_advance`, `uio.h:uio_copyfrom`, `uio.h:uio_copyto` - Vectored I/O (`iovec`) state tracking and buffer copy utilities.
- `fat.h:fat_getattrib`, `fat.h:fat_setattrib`, `hostfs.h:host_open`, `nfs.h:nfs_args`, `nxffs.h:nxffs_initialize`, `smart.h:smart_format_s`, `userfs.h:userfs_operations_s`, `userfs.h:userfs_run`, `xipfs.h:xipfs_extent_info_s` - Filesystem-specific control structures and initialization routines.

## Invariants
- `ioctl.h:_IOC_MASK` reserves the lower 8 bits (`0x00ff`) for the command number and the upper bits for the subsystem base (`_TIOCBASE` .. `_BOARDBASE`).
- `fs.h:inode` type flags (`FSNODEFLAG_TYPE_MASK`) are mutually exclusive and inspected via `INODE_IS_*` macros before dereferencing `i_ops` union members (`u.i_ops`, `u.i_bops`, `u.i_mops`).

## Side Effects
- `fs.h:register_driver`, `fs.h:register_blockdriver`, and `fs.h:nx_mount` mutate the global VFS inode tree under lock.
- `fs.h:file_open`, `fs.h:file_write`, `fs.h:file_ioctl`, `hostfs.h:host_*`, and `userfs.h:userfs_run` perform underlying storage I/O, host OS syscalls (in Simulator builds), or local UDP socket IPC (for UserFS).

## Verification
- Run: `make test`
