# Host File System (HostFS)

## Overview
Implements a pass-through filesystem (`g_hostfs_operations`) primarily used in the NuttX simulator (`sim`) and semihosting environments to mount a directory from the host operating system into the NuttX VFS hierarchy.

## Interface
- `hostfs.c:g_hostfs_operations` - VFS mountpoint operations table (`struct mountpt_operations`) forwarding file and directory calls to host OS interfaces.
- `hostfs.h:struct hostfs_mountpt_s`, `hostfs.h:struct hostfs_ofile_s`, `hostfs.h:HOSTFS_MAX_PATH` - Mountpoint state, open-file list node, and path length limit.

## Invariants
- Access to a mountpoint's open-file list (`fs_head`) and host operations is serialized by `fs_lock` (`hostfs.h:struct hostfs_mountpt_s`).
- Relative paths passed into `hostfs.c:hostfs_mkpath` are pre-canonicalized by the VFS layer and concatenated onto `fs->fs_root` within `HOSTFS_MAX_PATH` bounds.

## Side Effects
- Invokes host OS system call wrappers (`host_open`, `host_close`, `host_read`, `host_write`, `host_lseek`, `host_ioctl`, `host_sync`, `host_fstat`, `host_ftruncate`, `host_opendir`, `host_readdir`, `host_closedir`, `host_statfs`, `host_unlink`, `host_mkdir`, `host_rmdir`, `host_rename`, `host_stat`, `host_chstat`, `host_link`, `host_symlink`, `host_readlink`) affecting the underlying host filesystem.
- Allocates and frees mountpoint, directory, and open-file structures on the filesystem heap (`fs_heap_malloc`, `fs_heap_zalloc`, `fs_heap_free`) and temporary path buffers (`lib_get_tempbuffer`, `lib_put_tempbuffer`).

## Verification
- Run: `make test`
