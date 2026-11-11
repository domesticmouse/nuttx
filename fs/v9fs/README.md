# Plan 9 (9P2000.L) Remote File System Client (`fs/v9fs`)

## Overview
Implements the 9P2000.L (`v9fs`) network/virtualization filesystem client, decoupling VFS and 9P protocol FID management (`client.c`) from pluggable lower-half transports (`virtio_9p.c` for VirtIO and `socket_9p.c` for TCP sockets).

## Interface
- `v9fs.c:g_v9fs_operations` - Global `struct mountpt_operations` table implementing VFS operations for `v9fs` (`v9fs_vfs_open`, `v9fs_vfs_close`, `v9fs_vfs_read`, `v9fs_vfs_write`, `v9fs_vfs_seek`, `v9fs_vfs_ioctl`, `v9fs_vfs_truncate`, `v9fs_vfs_sync`, `v9fs_vfs_dup`, `v9fs_vfs_fstat`, `v9fs_vfs_fchstat`, `v9fs_vfs_opendir`, `v9fs_vfs_closedir`, `v9fs_vfs_readdir`, `v9fs_vfs_rewinddir`, `v9fs_vfs_bind`, `v9fs_vfs_unbind`, `v9fs_vfs_statfs`, `v9fs_vfs_unlink`, `v9fs_vfs_mkdir`, `v9fs_vfs_rmdir`, `v9fs_vfs_rename`, `v9fs_vfs_stat`, `v9fs_vfs_chstat`, `v9fs_vfs_link`, `v9fs_vfs_symlink`, `v9fs_vfs_readlink`, `v9fs_vfs_lstat`).
- `client.h:struct v9fs_client_s` - Per-mountpoint 9P client state tracking the active `struct v9fs_transport_s *`, FID allocator (`struct idr_s *fids`), negotiated maximum message size (`msize`), `root_fid`, and client `lock`.
- `client.h:v9fs_client_init`, `client.h:v9fs_client_uninit` - Initializes/uninitializes a 9P client session, parsing mount options, creating the transport, and executing `Tversion` and `Tattach` handshakes.
- `client.h:v9fs_client_walk`, `client.h:v9fs_client_open`, `client.h:v9fs_client_create`, `client.h:v9fs_client_read`, `client.h:v9fs_client_write`, `client.h:v9fs_client_readdir`, `client.h:v9fs_client_stat`, `client.h:v9fs_client_statfs`, `client.h:v9fs_client_chstat`, `client.h:v9fs_client_fsync`, `client.h:v9fs_client_mkdir`, `client.h:v9fs_client_unlink`, `client.h:v9fs_client_rename`, `client.h:v9fs_client_remove`, `client.h:v9fs_client_symlink`, `client.h:v9fs_client_link`, `client.h:v9fs_client_readlink` - 9P2000.L protocol RPC operations.
- `client.h:v9fs_transport_create`, `client.h:v9fs_transport_request`, `client.h:v9fs_transport_destroy`, `client.h:v9fs_transport_done` - Transport abstraction layer dispatching to `virtio` or `tcp` transport implementations.

## Invariants
- FIDs (`uint32_t fid`) are allocated via `idr_alloc_u32` under `client->lock` and reference-counted (`v9fs_fid_get` / `v9fs_fid_put`); when a FID's reference count reaches zero, a `Tclunk` RPC is issued to release it on the server.
- Each in-flight `struct v9fs_payload_s` blocks on its response semaphore (`resp`) until the lower-half transport invokes `v9fs_transport_done`.

## Side Effects
- Allocates and frees FIDs (`idr_init`, `idr_destroy`), client structures, and I/O buffers on the filesystem heap (`fs_heap_zalloc`, `fs_heap_malloc`, `fs_heap_free`).
- Transmits and receives 9P protocol frames over VirtIO queues (`virtqueue_add_buffer`, `virtqueue_kick`) or kernel TCP sockets (`psock_send`, `psock_recv`).

## Verification
- Run: `make test`
