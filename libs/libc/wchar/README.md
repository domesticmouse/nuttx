# Wide-Character & Multibyte String Operations (`libs/libc/wchar`)

## Overview
Implements ISO C99 and POSIX `<wchar.h>` wide-character string manipulation, wide-memory operations, UTF-8 multibyte-to-wide-character stateful conversions (`mbrtowc`, `wcrtomb`, `mbsrtowcs`, `wcsrtombs`), wide-character numeric parsing (`wcsto*`), formatted wide string output (`swprintf`, `vswprintf`, `wcsftime`), and display width calculation (`wcwidth`, `wcswidth`).

## Interface
- `lib_mbrtowc.c:mbrtowc`, `lib_wcrtomb.c:wcrtomb`, `lib_mbrlen.c:mbrlen`, `lib_mbsinit.c:mbsinit`, `lib_btowc.c:btowc`, `lib_wctob.c:wctob`, `lib_mbsrtowcs.c:mbsrtowcs`, `lib_mbsnrtowcs.c:mbsnrtowcs`, `lib_wcsrtombs.c:wcsrtombs`, `lib_wcsnrtombs.c:wcsnrtombs` - Stateful UTF-8 / `wchar_t` (`mbstate_t`) character and string conversion functions.
- `lib_wcslen.c:wcslen`, `lib_wcsnlen.c:wcsnlen`, `lib_wcscpy.c:wcscpy`, `lib_wcsncpy.c:wcsncpy`, `lib_wcslcpy.c:wcslcpy`, `lib_wcpcpy.c:wcpcpy`, `lib_wcpncpy.c:wcpncpy`, `lib_wcscat.c:wcscat`, `lib_wcsncat.c:wcsncat`, `lib_wcslcat.c:wcslcat`, `lib_wcsdup.c:wcsdup` - Wide string length, copy, concatenation, and heap duplication (`lib_malloc`).
- `lib_wcscmp.c:wcscmp`, `lib_wcsncmp.c:wcsncmp`, `lib_wcscasecmp.c:wcscasecmp`, `lib_wcsncasecmp.c:wcsncasecmp`, `lib_wcscoll.c:wcscoll`, `lib_wcsxfrm.c:wcsxfrm` - Wide string comparisons and locale transformations.
- `lib_wcschr.c:wcschr`, `lib_wcsrchr.c:wcsrchr`, `lib_wcscspn.c:wcscspn`, `lib_wcsspn.c:wcsspn`, `lib_wcspbrk.c:wcspbrk`, `lib_wcsstr.c:wcsstr`, `lib_wcswcs.c:wcswcs`, `lib_wcstok.c:wcstok` - Wide string search and reentrant tokenization.
- `lib_wmemcpy.c:wmemcpy`, `lib_wmemmove.c:wmemmove`, `lib_wmemset.c:wmemset`, `lib_wmemcmp.c:wmemcmp`, `lib_wmemchr.c:wmemchr` - Wide-character array (`wchar_t *`) memory operations.
- `lib_wcstol.c:wcstol`, `lib_wcstoll.c:wcstoll`, `lib_wcstoul.c:wcstoul`, `lib_wcstoull.c:wcstoull`, `lib_wcstof.c:wcstof`, `lib_wcstod.c:wcstod`, `lib_wcstold.c:wcstold` - Wide string to integer and floating-point conversions.
- `lib_swprintf.c:swprintf`, `lib_swprintf.c:vswprintf`, `lib_wcsftime.c:wcsftime`, `lib_wcwidth.c:wcwidth`, `lib_wcswidth.c:wcswidth` - Wide formatted output, date/time formatting, and Unicode terminal column width queries.

## Invariants
- `lib_mbrtowc.c:mbrtowc` and `lib_wcrtomb.c:wcrtomb` reject overlong UTF-8 sequences, UTF-16 surrogate code points (`0xd800`..`0xdfff`), and code points above `0x10ffff`, returning `(size_t)-1` with `errno = EILSEQ`.

## Side Effects
- Mutates destination `wchar_t`/multibyte buffers and `mbstate_t` conversion states (falling back to function-static `mbstate_t` when `ps == NULL`), sets `errno = EILSEQ` or `ERANGE` on conversion errors, and allocates heap memory in `lib_wcsdup.c:wcsdup` (`lib_malloc`).

## Verification
- Run: `make test`
