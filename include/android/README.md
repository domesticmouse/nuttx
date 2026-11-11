# Android Compatibility Headers (`include/android`)

## Overview
Provides Android Bionic compatibility declarations (`fdsan.h`) for file descriptor sanitizer (`fdsan`) ownership tag creation, exchange, and checked closure on NuttX.

## Interface
- `fdsan.h:android_fdsan_owner_type`, `fdsan.h:android_fdsan_owner_type_t` - Enumeration of file descriptor owner types (`ANDROID_FDSAN_OWNER_TYPE_FILE`, `ANDROID_FDSAN_OWNER_TYPE_DIR`, `ANDROID_FDSAN_OWNER_TYPE_UNIQUE_FD`, `ANDROID_FDSAN_OWNER_TYPE_SQLITE`, etc.).
- `fdsan.h:android_fdsan_create_owner_tag`, `fdsan.h:android_fdsan_exchange_owner_tag`, `fdsan.h:android_fdsan_close_with_tag` - Ownership tag encoding, atomic tag exchange on an open file descriptor, and tag-verified `close()`.

## Invariants
- A 64-bit owner tag created via `fdsan.h:android_fdsan_create_owner_tag` encodes the 8-bit `android_fdsan_owner_type` in its most significant byte and the lower 56 bits of the owner address in bits `0..55`.
- Closing a tagged descriptor via `fdsan.h:android_fdsan_close_with_tag` requires `tag` to match the descriptor's current `expected_tag` stored by `fdsan.h:android_fdsan_exchange_owner_tag`.

## Side Effects
- `fdsan.h:android_fdsan_exchange_owner_tag` mutates the file descriptor's recorded ownership tag in the process file table.
- `fdsan.h:android_fdsan_close_with_tag` closes the underlying OS file descriptor and logs/traps on ownership tag mismatch.

## Verification
- Run: `make test`
