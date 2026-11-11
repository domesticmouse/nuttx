# Network File System (NFSv3) Client (`fs/nfs`)

## Overview
Implements an NFS Version 3 client filesystem over UDP/RPC (`struct rpcclnt`), allowing NuttX to mount and access remote NFSv3 exports via standard VFS operations.

## Interface
- `nfs_vfsops.c:g_nfs_operations` - Global `struct mountpt_operations` table implementing NFSv3 VFS operations (`nfs_open`, `nfs_close`, `nfs_read`, `nfs_write`, `nfs_seek`, `nfs_dup`, `nfs_fstat`, `nfs_fchstat`, `nfs_truncate`, `nfs_opendir`, `nfs_closedir`, `nfs_readdir`, `nfs_rewinddir`, `nfs_bind`, `nfs_unbind`, `nfs_statfs`, `nfs_unlink`, `nfs_mkdir`, `nfs_rmdir`, `nfs_rename`, `nfs_stat`, `nfs_chstat`).
- `nfs_vfsops.c:nfsstats` - Global `struct nfsstats` structure tracking RPC and NFS procedure call statistics.
- `nfs.h:struct nfsmount` - Per-mountpoint state holding the open file list, RPC client handle (`nm_rpcclnt`), root file handle (`nm_fh`), server address, and transfer size parameters.
- `nfs.h:nfs_request` - Performs an RPC call to the remote NFS server using the mountpoint's RPC client.
- `nfs.h:nfs_lookup` - Executes an `NFSPROC_LOOKUP` RPC to resolve a filename within a directory file handle.
- `nfs.h:nfs_findnode` - Traverses a relative path from the root file handle to resolve the target file handle and attributes.
- `nfs.h:nfs_finddir` - Traverses a relative path to resolve the parent directory file handle and leaf filename for creation/deletion operations.
- `nfs.h:nfs_attrupdate` - Updates cached file attributes inside an open `struct nfsnode` from an NFSv3 `fattr3` response.
- `rpc_clnt.c:rpcclnt_init` - Allocates and initializes an `rpcclnt` structure.
- `rpc_clnt.c:rpcclnt_connect` - Opens a UDP socket, queries the remote portmapper/mountd, and mounts the remote NFS export.
- `rpc_clnt.c:rpcclnt_disconnect` - Unmounts the remote export and closes the RPC UDP socket.
- `rpc_clnt.c:rpcclnt_request` - Sends an XDR-encoded RPC request over the UDP socket with timeout and retransmission handling.

## Invariants
- `nfs.h:struct nfsmount` serializes concurrent VFS operations and shared RPC buffer (`nm_iobuffer`) usage using a per-mountpoint mutex (`nm_lock`).
- `nfs_vfsops.c:nfs_unbind` refuses to unmount (`-EBUSY`) if `nfsmount->nm_head` contains any open file structures unless `MNT_FORCE` is set.

## Side Effects
- Sends and receives RPC/XDR network packets over kernel UDP sockets (`psock_sendto`, `psock_recvfrom`, `psock_socket`, `psock_close`).
- Allocates and frees mountpoint, RPC client, file node (`struct nfsnode`), and directory structures on the filesystem heap (`fs_heap_zalloc`, `fs_heap_free`).
- Updates global RPC/NFS counters in `nfsstats`.

## Verification
- Run: `make test`
