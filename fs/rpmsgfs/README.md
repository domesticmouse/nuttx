# Remote Processor Messaging File System (`fs/rpmsgfs`)

## Overview
Implements the RPMsg remote filesystem (`rpmsgfs`) client and server over OpenAMP/RPMsg channels, allowing a NuttX processor to mount and operate on a filesystem hosted by a remote core.

## Interface
- `rpmsgfs.c:g_rpmsgfs_operations` - Global `struct mountpt_operations` table implementing VFS operations (`rpmsgfs_open`, `rpmsgfs_close`, `rpmsgfs_read`, `rpmsgfs_write`, `rpmsgfs_seek`, `rpmsgfs_ioctl`, `rpmsgfs_truncate`, `rpmsgfs_sync`, `rpmsgfs_dup`, `rpmsgfs_fstat`, `rpmsgfs_fchstat`, `rpmsgfs_opendir`, `rpmsgfs_closedir`, `rpmsgfs_readdir`, `rpmsgfs_rewinddir`, `rpmsgfs_bind`, `rpmsgfs_unbind`, `rpmsgfs_statfs`, `rpmsgfs_unlink`, `rpmsgfs_mkdir`, `rpmsgfs_rmdir`, `rpmsgfs_rename`, `rpmsgfs_stat`, `rpmsgfs_chstat`, `rpmsgfs_link`, `rpmsgfs_symlink`, `rpmsgfs_readlink`, `rpmsgfs_lstat`).
- `rpmsgfs.h:rpmsgfs_server_init` - Registers the RPMsg endpoint service handler on the host/server processor to service incoming `RPMSGFS_*` commands.
- `rpmsgfs.h:rpmsgfs_client_bind`, `rpmsgfs.h:rpmsgfs_client_unbind` - Binds and unbinds an RPMsg client endpoint to the target `cpuname` (`"rpmsgfs-<pid>"`).
- `rpmsgfs.h:rpmsgfs_client_open`, `rpmsgfs.h:rpmsgfs_client_close`, `rpmsgfs.h:rpmsgfs_client_read`, `rpmsgfs.h:rpmsgfs_client_write`, `rpmsgfs.h:rpmsgfs_client_lseek`, `rpmsgfs.h:rpmsgfs_client_ioctl`, `rpmsgfs.h:rpmsgfs_client_sync`, `rpmsgfs.h:rpmsgfs_client_dup`, `rpmsgfs.h:rpmsgfs_client_fstat`, `rpmsgfs.h:rpmsgfs_client_fchstat`, `rpmsgfs.h:rpmsgfs_client_ftruncate`, `rpmsgfs.h:rpmsgfs_client_opendir`, `rpmsgfs.h:rpmsgfs_client_readdir`, `rpmsgfs.h:rpmsgfs_client_rewinddir`, `rpmsgfs.h:rpmsgfs_client_closedir`, `rpmsgfs.h:rpmsgfs_client_statfs`, `rpmsgfs.h:rpmsgfs_client_unlink`, `rpmsgfs.h:rpmsgfs_client_mkdir`, `rpmsgfs.h:rpmsgfs_client_rmdir`, `rpmsgfs.h:rpmsgfs_client_rename`, `rpmsgfs.h:rpmsgfs_client_stat`, `rpmsgfs.h:rpmsgfs_client_chstat` - Client-side RPC transport functions.

## Invariants
- `rpmsgfs.c:struct rpmsgfs_mountpt_s` protects the open file list (`fs_head`) with `fs_lock` (`nxmutex_lock`).
- `rpmsgfs.c:rpmsgfs_unbind` refuses to unmount (`-EBUSY`) if `fs->fs_head` is non-NULL (open files exist).
- All wire messages begin with `struct rpmsgfs_header_s` (`command`, `result`, `cookie`) and use fixed-width packed fields (`struct rpmsgfs_stat_priv_s`) for cross-architecture ABI safety.

## Side Effects
- Registers RPMsg client/server callbacks (`rpmsg_register_callback`) and transmits/receives inter-processor RPMsg buffers (`rpmsg_send_nocopy`, `rpmsg_get_tx_payload_buffer`).
- On the server (`rpmsgfs_server.c`), executes real local VFS operations (`file_open`, `file_read`, `file_write`, `nx_mkdir`, `nx_unlink`, etc.) on behalf of the remote client.

## Verification
- Run: `make test`
