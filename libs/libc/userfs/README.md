# User-Space File System Server (`libs/libc/userfs`)

## Overview
Implements the user-space RPC server loop (`userfs_run`) for the NuttX UserFS proxy filesystem, registering a kernel mountpoint via `/dev/userfs` and dispatching incoming localhost UDP filesystem requests (`open`, `close`, `read`, `write`, `seek`, `ioctl`, `sync`, `dup`, `fstat`, `truncate`, `opendir`, `closedir`, `readdir`, `rewinddir`, `statfs`, `unlink`, `mkdir`, `rmdir`, `rename`, `stat`, `destroy`, `fchstat`, `chstat`) to caller-supplied `struct userfs_operations_s` callbacks.

## Interface
- `lib_userfs.c:userfs_run` - Allocates a `struct userfs_info_s` session context, opens a localhost `AF_INET` `SOCK_DGRAM` socket bound to `127.0.0.1`, registers the mountpoint via `ioctl(fd, FIOC_REGISTER, &config)` on `/dev/userfs`, and enters the request-dispatch and response-transmission loop until `USERFS_REQ_DESTROY` or an error occurs.

## Invariants
- `lib_userfs.c:userfs_run` and its `userfs_*_dispatch` helpers assert `DEBUGASSERT(info->userops != NULL && info->userops-><op> != NULL)` before invoking each filesystem operation callback and assert that `sendto` transmits the exact response header/payload size.

## Side Effects
- Allocates heap memory (`lib_malloc`/`lib_free`), creates and binds a localhost UDP socket (`socket`, `bind`, `recvfrom`, `sendto`, `close`), opens `/dev/userfs` and issues `FIOC_REGISTER` `ioctl` to mount the kernel proxy file system, and invokes user-supplied filesystem callbacks.

## Verification
- Run: `make test`
