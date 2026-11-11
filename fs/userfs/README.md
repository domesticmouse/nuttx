# User-Space File System Proxy (`fs/userfs`)

## Overview
Implements the kernel-side VFS proxy (`userfs`) that forwards filesystem operations as UDP request/response packets over local loopback (`127.0.0.1`) to a user-space filesystem daemon created via `userfs_run()`.

## Interface
- `fs_userfs.c:g_userfs_operations` - Global `struct mountpt_operations` table forwarding VFS calls (`userfs_open`, `userfs_close`, `userfs_read`, `userfs_write`, `userfs_seek`, `userfs_ioctl`, `userfs_truncate`, `userfs_sync`, `userfs_dup`, `userfs_fstat`, `userfs_fchstat`, `userfs_opendir`, `userfs_closedir`, `userfs_readdir`, `userfs_rewinddir`, `userfs_bind`, `userfs_unbind`, `userfs_statfs`, `userfs_unlink`, `userfs_mkdir`, `userfs_rmdir`, `userfs_rename`, `userfs_stat`, `userfs_chstat`) over a kernel UDP socket.
- `fs_userfs.c:struct userfs_state_s` - Holds the per-mountpoint UDP client socket (`psock`), server `sockaddr_in` (`127.0.0.1:portno`), serialization mutex (`lock`), maximum write payload size (`mxwrite`), and shared `iobuffer`.

## Invariants
- `fs_userfs.c:userfs_bind` requires a non-NULL `struct userfs_config_s *` passed via `data` and serializes all request/response exchanges through `priv->lock` (`nxmutex_lock`) because `priv->iobuffer` and `priv->psock` are shared across the mountpoint.
- Relative path lengths passed to `userfs` operations must not exceed `priv->mxwrite` (`-E2BIG` otherwise).

## Side Effects
- Creates and closes an internal `PF_INET` `SOCK_DGRAM` kernel socket (`psock_socket`, `psock_close`) and exchanges request/response datagrams (`psock_sendto`, `psock_recvfrom`) with the user-space server on `INADDR_LOOPBACK`.
- Allocates `struct userfs_state_s` and directory handles (`struct userfs_dir_s`) from the filesystem heap (`fs_heap_zalloc`, `fs_heap_malloc`, `fs_heap_free`).

## Verification
- Run: `make test`
