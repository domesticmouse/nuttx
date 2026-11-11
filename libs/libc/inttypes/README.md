# Fixed-Width Integer Arithmetic and Conversion (`libs/libc/inttypes`)

## Overview
Implements the standard C99 `<inttypes.h>` operations on greatest-width integers (`intmax_t` and `uintmax_t`), including absolute value (`imaxabs`), quotient/remainder division (`imaxdiv`), and string-to-integer parsing (`strtoimax`, `strtoumax`).

## Interface
- `[lib_imaxabs.c:imaxabs]` - Computes the absolute value of `intmax_t` argument `j`.
- `[lib_imaxdiv.c:imaxdiv]` - Computes the quotient (`quot`) and remainder (`rem`) of `numer / denom` in a single `imaxdiv_t` result.
- `[lib_strtoimax.c:strtoimax]` - Parses the initial portion of string `nptr` into a signed `intmax_t` value using radix `base`.
- `[lib_strtoumax.c:strtoumax]` - Parses the initial portion of string `nptr` into an unsigned `uintmax_t` value using radix `base`.

## Invariants
- `base` passed to `[lib_strtoimax.c:strtoimax]` and `[lib_strtoumax.c:strtoumax]` must be `0` or in the range `[2, 36]`.
- `denom` passed to `[lib_imaxdiv.c:imaxdiv]` must be non-zero.

## Side Effects
- `[lib_strtoimax.c:strtoimax]` and `[lib_strtoumax.c:strtoumax]` set thread `errno` via `set_errno()` to `EINVAL` on an unsupported base or `ERANGE` when the parsed value overflows `INTMAX_MAX`, `INTMAX_MIN`, or `UINTMAX_MAX`.

## Verification
- Run: `make test`
