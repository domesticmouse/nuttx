# Vectored Scatter/Gather Offset I/O (`libs/libc/uio`)

## Overview
Implements BSD/POSIX `<sys/uio.h>` positional scatter/gather I/O functions (`preadv` and `pwritev`) that read or write across an array of `struct iovec` buffers at an explicit file offset without relying on sequential caller loops.

## Interface
- `lib_preadv.c:preadv` - Reads data from file descriptor `fildes` at `offset` sequentially into `iovcnt` buffers in `iov[]` via `pread`.
- `lib_pwritev.c:pwritev` - Writes data from `iovcnt` buffers in `iov[]` sequentially to file descriptor `fildes` at `offset` via `pwrite`.

## Invariants
- Both `lib_preadv.c:preadv` and `lib_pwritev.c:pwritev` skip zero-length `iov[i].iov_len` entries and return the total byte count transferred if a partial transfer or error occurs after at least one byte has been read or written.

## Side Effects
- Performs positional file descriptor reads and writes via `pread` and `pwrite` system calls and updates `errno` on failure.

## Verification
- Run: `make test`
