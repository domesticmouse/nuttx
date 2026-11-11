# pic32

## Overview
Host-side post-build Intel HEX address conversion utility (`tools/pic32`) for Microchip PIC32 targets. Adjusts Extended Linear Address records in `nuttx.hex` from virtual KSEG addresses to 29-bit physical addresses expected by PIC32 flash programmers.

## Interface
- `mkpichex.c:main` - CLI entry point (`mkpichex <topdir-path>`) that reads `<topdir>/nuttx.hex`, converts Extended Linear Address records, and writes the updated `<topdir>/nuttx.hex`.
- `mkpichex.c:hex_s`, `mkpichex.c:parse_line`, `mkpichex.c:adjust_extlin` - Intel HEX record parser and Extended Linear Address (`TYPE_EXTLIN = 4`) transformer that masks the upper 16-bit address segment with `0x1fff` and recomputes the record two's-complement checksum.
- `Config.mk:POSTBUILD` - Build system macro that compiles `mkpichex` via `Makefile.host` and executes it on `nuttx.hex`.

## Invariants
- Extended Linear Address records (`TYPE_EXTLIN = 4`) must have `len == 2` and `addr == 0`; otherwise `mkpichex.c:adjust_extlin` reports an error and exits non-zero.
- Each Intel HEX input line must start with `:` and stay within `MAX_LINE` (`1024` bytes).

## Side Effects
- Creates `<topdir>/nuttx.tmp`, unlinks the original `<topdir>/nuttx.hex`, and renames `<topdir>/nuttx.tmp` to `<topdir>/nuttx.hex`.

## Verification
- Run: `make test`
