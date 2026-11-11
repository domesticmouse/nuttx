# Intel HEX to Binary Conversion (`libs/libc/hex2bin`)

## Overview
Implements Intel HEX ASCII stream parsing and binary conversion routines (`hex2bin`, `data2bin`, `hex2mem`, `fhex2mem`) declared in `<hex2bin.h>` when `CONFIG_LIBC_HEX2BIN` is enabled. Supports standard 16-bit addresses as well as Extended Segment Address (`02`), Extended Linear Address (`04`), and Start Linear Address (`05`) records, with configurable byte-order swapping.

## Interface
- `[lib_hex2bin.c:hex2bin]` - Reads an Intel HEX stream from `instream` and writes the decoded binary data to `outstream` within `[baseaddr, endpaddr)`.
- `[lib_hex2bin.c:data2bin]` - Decodes an in-memory buffer `src` of Intel HEX data into `dst` within `[baseaddr, endpaddr)`.
- `[lib_hex2mem.c:hex2mem]` - Reads an Intel HEX stream from file descriptor `fd` and writes the decoded binary payload directly into memory `[baseaddr, endpaddr)`.
- `[lib_fhex2mem.c:fhex2mem]` - Reads an Intel HEX `FILE *instream` and writes the decoded binary payload directly into memory `[baseaddr, endpaddr)`.

## Invariants
- If `endpaddr != 0`, `endpaddr` must be `>= baseaddr` (`[lib_hex2bin.c:hex2bin]`, `[lib_hex2mem.c:hex2mem]`, `[lib_fhex2mem.c:fhex2mem]`).
- Every Intel HEX record must start with `':'` and have a valid two's-complement checksum summing to `0`; malformed records abort parsing with `-EINVAL`.

## Side Effects
- `[lib_hex2bin.c:hex2bin]` allocates and frees a working line buffer via `lib_malloc()` and `lib_free()`.
- Reads from `FILE *` streams (`fgetc`, `fseek`) or file descriptors and writes decoded binary bytes directly to `outstream` or target memory addresses (`(uint8_t *)(uintptr_t)addr`) (`[lib_hex2bin.c:hex2bin]`, `[lib_hex2mem.c:hex2mem]`, `[lib_fhex2mem.c:fhex2mem]`).

## Verification
- Run: `make test`
