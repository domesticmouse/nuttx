# Thread-Local Error Number Accessor (`libs/libc/errno`)

## Overview
Provides the `__errno()` accessor function backing the standard `<errno.h>` `errno` macro in NuttX. Resolves the calling thread's `tl_errno` storage location from Thread-Local Storage (TLS) with a static fallback for early boot or non-TLS contexts.

## Interface
- `[lib_errno.c:__errno]` - Returns a non-NULL `FAR int *` pointer to the current thread's `errno` variable (`tlsinfo->tl_errno`), or to a fallback static `s_errno` if `tls_get_info()` returns `NULL`.

## Invariants
- `[lib_errno.c:__errno]` always returns a valid, dereferenceable `int *` pointer even before TLS is initialized.

## Side Effects
- Queries thread-local storage via `tls_get_info()` (`[lib_errno.c:__errno]`).

## Verification
- Run: `make test`
