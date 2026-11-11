# Character Classification and Case Conversion (`libs/libc/ctype`)

## Overview
Implements standard C `<ctype.h>` character classification and case conversion functions along with their POSIX locale-aware (`*_l`) counterparts and the Newlib-compatible `_ctype_` lookup table.

## Interface
- `[lib_ctype.c:_ctype_]` - 257-byte character attribute lookup table used when `CONFIG_LIBC_ARCH_CTYPE` is enabled.
- `[lib_isalnum.c:isalnum]`, `[lib_isalnum.c:isalnum_l]` - Checks for an alphanumeric character.
- `[lib_isalpha.c:isalpha]`, `[lib_isalpha.c:isalpha_l]` - Checks for an alphabetic character.
- `[lib_isascii.c:isascii]`, `[lib_isascii.c:isascii_l]` - Checks whether `c` is a 7-bit US-ASCII character code (`0..0x7f`).
- `[lib_isblank.c:isblank]`, `[lib_isblank.c:isblank_l]` - Checks for a blank character (space or horizontal tab).
- `[lib_iscntrl.c:iscntrl]`, `[lib_iscntrl.c:iscntrl_l]` - Checks for a control character.
- `[lib_isdigit.c:isdigit]`, `[lib_isdigit.c:isdigit_l]` - Checks for a decimal digit (`'0'..'9'`).
- `[lib_isgraph.c:isgraph]`, `[lib_isgraph.c:isgraph_l]` - Checks for any printable character except space.
- `[lib_islower.c:islower]`, `[lib_islower.c:islower_l]` - Checks for a lowercase letter (`'a'..'z'`).
- `[lib_isprint.c:isprint]`, `[lib_isprint.c:isprint_l]` - Checks for any printable character including space.
- `[lib_ispunct.c:ispunct]`, `[lib_ispunct.c:ispunct_l]` - Checks for any printable character that is neither space nor alphanumeric.
- `[lib_isspace.c:isspace]`, `[lib_isspace.c:isspace_l]` - Checks for white-space characters.
- `[lib_isupper.c:isupper]`, `[lib_isupper.c:isupper_l]` - Checks for an uppercase letter (`'A'..'Z'`).
- `[lib_isxdigit.c:isxdigit]`, `[lib_isxdigit.c:isxdigit_l]` - Checks for a hexadecimal digit (`'0'..'9'`, `'a'..'f'`, `'A'..'F'`).
- `[lib_tolower.c:tolower]`, `[lib_tolower.c:tolower_l]` - Converts an uppercase letter to lowercase.
- `[lib_toupper.c:toupper]`, `[lib_toupper.c:toupper_l]` - Converts a lowercase letter to uppercase.

## Invariants
- All classification and case-conversion functions are stateless, pure operations following 7-bit US-ASCII rules; the `locale_t` parameter in `*_l` variants is ignored (`[lib_isalnum.c:isalnum_l]`, `[lib_tolower.c:tolower_l]`).

## Side Effects
- None

## Verification
- Run: `make test`
