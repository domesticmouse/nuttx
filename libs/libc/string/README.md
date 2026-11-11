# String & Memory Manipulation (`libs/libc/string`)

## Overview
Implements ISO C, POSIX, and BSD `<string.h>` and `<strings.h>` byte-string and raw-memory manipulation routines, bit-scanning/population-count intrinsics (`ffs*`, `fls*`, `popcount*`), error and signal number description lookups (`strerror`, `strsignal`), and word-aligned/BSD-optimized fallback implementations when architecture-specific assembly (`CONFIG_LIBC_ARCH_*`) is not enabled.

## Interface
- `lib_memcpy.c:memcpy`, `lib_bsdmemcpy.c:memcpy`, `lib_vikmemcpy.c:memcpy`, `lib_mempcpy.c:mempcpy`, `lib_memccpy.c:memccpy`, `lib_bsdmemccpy.c:memccpy`, `lib_memmove.c:memmove`, `lib_bcopy.c:bcopy` - Memory copy and overlapping memory move functions.
- `lib_memset.c:memset`, `lib_bsdmemset.c:memset`, `lib_bzero.c:bzero`, `lib_explicit_bzero.c:explicit_bzero` - Memory fill and compiler-barrier-protected zeroing (`explicit_bzero`).
- `lib_memcmp.c:memcmp`, `lib_bsdmemcmp.c:memcmp`, `lib_bcmp.c:bcmp`, `lib_timingsafe_bcmp.c:timingsafe_bcmp`, `lib_memchr.c:memchr`, `lib_bsdmemchr.c:memchr`, `lib_memrchr.c:memrchr`, `lib_bsdmemrchr.c:memrchr`, `lib_rawmemchr.c:rawmemchr`, `lib_memmem.c:memmem` - Memory comparison (including constant-time `timingsafe_bcmp`) and byte/subsequence search functions.
- `lib_strlen.c:strlen`, `lib_bsdstrlen.c:strlen`, `lib_strnlen.c:strnlen`, `lib_strcpy.c:strcpy`, `lib_bsdstrcpy.c:strcpy`, `lib_strncpy.c:strncpy`, `lib_bsdstrncpy.c:strncpy`, `lib_strlcpy.c:strlcpy`, `lib_stpcpy.c:stpcpy`, `lib_bsdstpcpy.c:stpcpy`, `lib_stpncpy.c:stpncpy`, `lib_bsdstpncpy.c:stpncpy`, `lib_strcat.c:strcat`, `lib_bsdstrcat.c:strcat`, `lib_strncat.c:strncat`, `lib_strlcat.c:strlcat` - String length, copying, and concatenation functions.
- `lib_strcmp.c:strcmp`, `lib_bsdstrcmp.c:strcmp`, `lib_strncmp.c:strncmp`, `lib_bsdstrncmp.c:strncmp`, `lib_strcasecmp.c:strcasecmp`, `lib_strncasecmp.c:strncasecmp`, `lib_strcoll.c:strcoll`, `lib_strxfrm.c:strxfrm`, `lib_strverscmp.c:strverscmp` - Lexicographical, case-insensitive, locale-aware, and version-ordered string comparisons.
- `lib_strchr.c:strchr`, `lib_bsdstrchr.c:strchr`, `lib_strchrnul.c:strchrnul`, `lib_bsdstrchrnul.c:strchrnul`, `lib_strrchr.c:strrchr`, `lib_bsdstrrchr.c:strrchr`, `lib_index.c:index`, `lib_rindex.c:rindex`, `lib_strstr.c:strstr`, `lib_strcasestr.c:strcasestr`, `lib_strpbrk.c:strpbrk`, `lib_strspn.c:strspn`, `lib_strcspn.c:strcspn`, `lib_strtok.c:strtok`, `lib_strtokr.c:strtok_r`, `lib_strsep.c:strsep` - Character/substring search and tokenization functions.
- `lib_strdup.c:strdup`, `lib_strdup.c:nx_strdup`, `lib_strndup.c:strndup`, `lib_strndup.c:nx_strndup` - Heap-allocated string duplication functions (`lib_malloc` vs `kmm_malloc`).
- `lib_strerror.c:strerror`, `lib_strerrorr.c:strerror_r`, `lib_strsignal.c:strsignal` - Translate `errno` and signal numbers to human-readable strings.
- `lib_ffs.c:ffs`, `lib_ffsl.c:ffsl`, `lib_ffsll.c:ffsll`, `lib_fls.c:fls`, `lib_flsl.c:flsl`, `lib_flsll.c:flsll`, `lib_popcount.c:popcount`, `lib_popcountl.c:popcountl`, `lib_popcountll.c:popcountll` - Find first/last bit set and population count (Hamming weight) operations.
- `lib_skipspace.c:lib_skipspace`, `lib_isbasedigit.c:lib_isbasedigit` - Internal libc parsing helpers for skipping whitespace and validating radix digits.

## Invariants
- `lib_timingsafe_bcmp.c:timingsafe_bcmp` inspects all `n` bytes without early termination so execution time is independent of byte values.
- `lib_explicit_bzero.c:explicit_bzero` inserts an optimization barrier after `memset(s, 0, n)` to prevent dead-store elimination.
- `lib_strerrorr.c:strerror_r` asserts `DEBUGASSERT(buf != NULL)`.

## Side Effects
- Destination buffers are mutated in place by copy, fill, and tokenization (`strtok`, `strtok_r`, `strsep`) routines.
- `lib_strdup.c:strdup`/`lib_strndup.c:strndup` allocate user heap memory via `lib_malloc` (setting `errno = ENOMEM` on failure), while `nx_strdup`/`nx_strndup` allocate via `kmm_malloc` without modifying `errno`.
- `lib_strtok.c:strtok`, `lib_strerror.c:strerror`, and `lib_strsignal.c:strsignal` mutate function-static state (`g_saveptr` or static fallback buffers).

## Verification
- Run: `make test`
