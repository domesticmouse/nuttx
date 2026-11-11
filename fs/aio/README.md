# POSIX Asynchronous I/O (AIO)

## Overview
Implements POSIX Asynchronous I/O (`CONFIG_FS_AIO`), scheduling non-blocking file read, write, fsync, and list I/O requests onto the NuttX low-priority work queue (`LPWORK`) and notifying client tasks via signals upon completion.

## Interface
- `aio.h:struct aio_container_s`, `aio.h:g_aio_pending` - Pre-allocated AIO control block wrapper and global doubly linked list of pending AIO operations.
- `aio.h:aio_initialize`, `aio.h:aio_lock`, `aio.h:aio_unlock` - Subsystem initialization and re-entrant lock management for `g_aio_pending`.
- `aio.h:aioc_alloc`, `aio.h:aioc_free`, `aio.h:aio_contain`, `aio.h:aioc_decant` - Allocation, wrapping, and release of `struct aio_container_s` instances around `struct aiocb`.
- `aio.h:aio_queue`, `aio.h:aio_signal` - Work queue scheduling and client completion signaling.
- `aio_read.c:aio_read`, `aio.h:aio_read_internal` - Enqueues asynchronous file read requests.
- `aio_write.c:aio_write`, `aio.h:aio_write_internal` - Enqueues asynchronous file write requests.
- `aio_fsync.c:aio_fsync` - Enqueues asynchronous file synchronization requests.
- `aio_cancel.c:aio_cancel` - Cancels pending asynchronous I/O requests matching a file descriptor or control block.
- `lio_listio.c:lio_listio` - Submits and optionally waits on a batch of asynchronous I/O requests.

## Invariants
- Access to `aio.h:g_aio_pending` must be serialized using `aio.h:aio_lock` and `aio.h:aio_unlock`.
- `aio.h:struct aio_container_s` pool size is bounded by `aio.h:CONFIG_FS_NAIOC`; `aio.h:aioc_alloc` blocks on a counting semaphore when all pre-allocated containers are in use.
- While an AIO operation is queued, `aiocbp->aio_result` is set to `-EINPROGRESS` until updated by the worker or `aio_cancel.c:aio_cancel`.

## Side Effects
- Schedules background work items on the `LPWORK` kernel work queue (`aio.h:aio_queue`, `aio_cancel.c:aio_cancel`).
- Performs VFS file operations (`file_read`, `file_pread`, `file_write`, `file_pwrite`, `file_fsync`) from worker thread context.
- Sends completion signals (`SIGPOLL` or user-configured `sigevent`) to waiting tasks (`aio.h:aio_signal`) and adjusts worker thread priorities when `CONFIG_PRIORITY_INHERITANCE` is enabled.

## Verification
- Run: `make test`
