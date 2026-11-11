# Asynchronous I/O (`libs/libc/aio`)

## Overview
Provides the C library user-space helpers for POSIX Asynchronous I/O (`<aio.h>`) enabled under `CONFIG_FS_AIO`. This component implements status querying (`aio_error`), final transfer result extraction (`aio_return`), and signal-driven caller suspension (`aio_suspend`) across arrays of `struct aiocb` control blocks.

## Interface
- `[aio.h:CONFIG_FS_AIO]` - Compile-time guard enabling POSIX asynchronous I/O support in `libc`.
- `[aio_error.c:aio_error]` - Returns the current error status (`EINPROGRESS`, `0`, or positive error code) of an asynchronous I/O control block (`aiocbp`).
- `[aio_return.c:aio_return]` - Returns the final `ssize_t` byte count or `-1` error status of a completed asynchronous I/O operation and invalidates subsequent calls on the same `aiocbp`.
- `[aio_suspend.c:aio_suspend]` - Suspends the calling thread until at least one asynchronous I/O request in `list` completes, a signal interrupts the wait, or an optional `timeout` expires.

## Invariants
- `aiocbp` passed to `[aio_error.c:aio_error]` and `[aio_return.c:aio_return]` must be non-NULL (`DEBUGASSERT(aiocbp)`).
- `aiocbp->aio_reqprio` must be `>= 0`; negative values cause `[aio_error.c:aio_error]` to fail with `EINVAL`.
- `[aio_return.c:aio_return]` may be called at most once per completed asynchronous I/O operation because it overwrites `aiocbp->aio_result` with `-EINVAL`.
- `list` passed to `[aio_suspend.c:aio_suspend]` must be non-NULL (`DEBUGASSERT(list)`).

## Side Effects
- `[aio_return.c:aio_return]` mutates `aiocbp->aio_result` to `-EINVAL` upon reading the completed result.
- `[aio_error.c:aio_error]`, `[aio_return.c:aio_return]`, and `[aio_suspend.c:aio_suspend]` set the calling thread's `errno` via `set_errno()` on error conditions.
- `[aio_suspend.c:aio_suspend]` queries `CLOCK_MONOTONIC` via `clock_gettime()` and blocks the calling thread waiting on `SIGPOLL` via `sigtimedwait()`.

## Verification
- Run: `make test`
