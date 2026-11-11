# Wide-Character Classification & Mapping (`libs/libc/wctype`)

## Overview
Implements ISO C99 and POSIX `<wctype.h>` wide-character classification (`isw*`, `iswctype`), property descriptor lookup (`wctype`), and case mapping (`towlower`, `towupper`) functions.

## Interface
- `lib_iswctype.c:iswalnum`, `lib_iswctype.c:iswalpha`, `lib_iswctype.c:iswblank`, `lib_iswctype.c:iswcntrl`, `lib_iswctype.c:iswdigit`, `lib_iswctype.c:iswgraph`, `lib_iswctype.c:iswlower`, `lib_iswctype.c:iswprint`, `lib_iswctype.c:iswpunct`, `lib_iswctype.c:iswspace`, `lib_iswctype.c:iswupper`, `lib_iswctype.c:iswxdigit`, `lib_iswctype.c:iswctype` - Classifies a `wint_t` wide character directly or against a `wctype_t` property (`WC_ALNUM`..`WC_XDIGIT`).
- `lib_wctype.c:wctype` - Maps a character class name string (`"alnum"`, `"alpha"`, `"blank"`, `"cntrl"`, `"digit"`, `"graph"`, `"lower"`, `"print"`, `"punct"`, `"space"`, `"upper"`, `"xdigit"`) to its `wctype_t` constant (or `0` if unrecognized).
- `lib_towlower.c:towlower`, `lib_towupper.c:towupper` - Converts a `wint_t` wide character to lowercase or uppercase.

## Invariants
- All functions in `libs/libc/wctype` are pure, stateless functions that return `0` (for classification/descriptor lookup) or the unchanged `wint_t` (for case conversion) on unrecognized or unmapped inputs.

## Side Effects
- None

## Verification
- Run: `make test`
