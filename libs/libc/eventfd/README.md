# Eventfd Counter I/O Helpers (`libs/libc/eventfd`)

## Overview
Implements the C library wrapper functions (`eventfd_read` and `eventfd_write`) for reading and writing 64-bit `eventfd_t` counter values on `<sys/eventfd.h>` file descriptors.

## Interface
- `[lib_eventfd.c:eventfd_read]` - Reads an `eventfd_t` counter value from file descriptor `fd` into `*value`, returning `0` on full read or `-1` on error.
- `[lib_eventfd.c:eventfd_write]` - Writes an `eventfd_t` counter increment `value` to file descriptor `fd`, returning `0` on full write or `-1` on error.

## Invariants
- Both `[lib_eventfd.c:eventfd_read]` and `[lib_eventfd.c:eventfd_write]` require the underlying transfer to equal `sizeof(eventfd_t)` bytes to return `0`.

## Side Effects
- Invokes the `read()` and `write()` system calls on file descriptor `fd` (`[lib_eventfd.c:eventfd_read]`, `[lib_eventfd.c:eventfd_write]`).

## Verification
- Run: `make test`
