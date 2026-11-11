# Filesystem Mount Management (`fs/mount`)

## Overview
Implements VFS mount and unmount operations, filesystem type lookup, mountpoint iteration, procfs mount table reporting, and interrupt-driven media automounting.

## Interface
- `fs_mount.c:nx_mount` - Internal kernel function to mount a filesystem at a target path with optional block/MTD driver binding.
- `fs_mount.c:mount` - Standard POSIX-like C library wrapper around `nx_mount` that sets `errno` on failure.
- `fs_umount2.c:nx_umount2` - Internal kernel function to unmount a filesystem at a target path with flags (`MNT_FORCE`, `MNT_DETACH`, `MNT_EXPIRE`, `UMOUNT_NOFOLLOW`).
- `fs_umount2.c:umount2` - Standard C library wrapper around `nx_umount2` that sets `errno` on failure.
- `mount.h:foreach_mountpoint` - Iterates over all active mountpoints in the VFS inode tree and invokes a `foreach_mountpoint_t` callback with `struct statfs` data.
- `mount.h:fs_gettype` - Returns the lowercase string name of a filesystem corresponding to `struct statfs.f_type` (`magic`).
- `fs_automount.c:automount_initialize` - Initializes the event-driven automounter on the work queue for removable media described by `struct automount_lower_s`.
- `fs_automount.c:automount_uninitialize` - Detaches the automounter interrupt handler, cancels pending work, and releases automounter state.
- `fs_procfs_mount.c:g_mount_operations` - Procfs operations table exposing `mount`, `blocks`, and `usage` virtual files.

## Invariants
- `fs_mount.c:nx_mount` requires `target` and `filesystemtype` to be non-NULL (`-EINVAL` otherwise) and verifies that the target inode does not already exist unless `MS_REMOUNT` is specified.
- `fs_umount2.c:nx_umount2` requires the resolved target inode to be a valid mountpoint (`INODE_IS_MOUNTPT(mountpt_inode)`), returning `-EINVAL` otherwise.
- `fs_automount.c:automount_initialize` asserts that `lower`, `lower->fstype`, `lower-> blockdev`, and `lower->mountpoint` are non-NULL (`DEBUGASSERT`).

## Side Effects
- `fs_mount.c:nx_mount` and `fs_umount2.c:nx_umount2` acquire the global inode tree lock via `inode_lock()` / `inode_unlock()`, allocate/free mountpoint inodes, invoke filesystem-specific `bind` and `unbind` callbacks, and notify inotify watchers (`notify_unmount`).
- `fs_automount.c:automount_initialize` allocates state from the kernel heap (`kmm_zalloc`), attaches media change interrupts via `AM_ATTACH`, and schedules mount/unmount retries on `LPWORK` (`work_queue`).

## Verification
- Run: `make test`
