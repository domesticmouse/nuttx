# Abstract Input/Output Streams (`libs/libc/stream`)

## Overview
Implements the NuttX internal polymorphic stream abstraction (`struct lib_instream_s`, `struct lib_outstream_s`, `struct lib_sistream_s`, `struct lib_sostream_s`) and concrete stream backends (memory, file, raw fd, stdio `FILE`, block device, MTD flash, null/zero, low-level console, syslog, buffered, hex dump, Base64, LZF compression), as well as the core formatted output (`lib_vsprintf`) and input (`lib_vscanf`) engines.

## Interface
- `lib_libvsprintf.c:lib_vsprintf`, `lib_libvsprintf.c:lib_vsprintf_internal`, `lib_libvsprintf.c:lib_sprintf`, `lib_libvsprintf.c:lib_sprintf_internal`, `lib_libbsprintf.c:lib_bsprintf` - Core `printf`-style formatting engine writing to any `struct lib_outstream_s` (supporting `%pS`/`%pB` symbol lookup, `%pV`, floating-point via `__dtoa_engine`/`__hexfloat_engine`, and packed binary arguments via `lib_bsprintf`).
- `lib_libvscanf.c:lib_vscanf`, `lib_libvscanf.c:lib_scanf`, `lib_libvscanf.c:lib_bscanf` - Core `scanf`-style parsing engine reading from any `struct lib_instream_s`.
- `lib_dtoa_engine.h:__dtoa_engine`, `lib_dtoa_bits.c:__dtoa_engine`, `lib_dtoa_big.c:__dtoa_big_start`, `lib_dtoa_big.c:__dtoa_big_start_ld`, `lib_dtoa_big.c:__dtoa_big_digit`, `lib_hexfloat.h:__hexfloat_engine`, `lib_hexfloat.h:__hexfloat_engine_ld`, `lib_hexfloat.c:__hexfloat_engine`, `lib_hexfloat.c:__hexfloat_engine_ld`, `lib_ultoa_invert.h:__ultoa_invert`, `lib_ultoa_invert.c:__ultoa_invert` - Exact and fast floating-point decimal/hexadecimal and integer conversion helpers for `lib_vsprintf`.
- `lib_meminstream.c:lib_meminstream`, `lib_memoutstream.c:lib_memoutstream`, `lib_memsistream.c:lib_memsistream`, `lib_memsostream.c:lib_memsostream` - Fixed-size memory buffer input, output, and seekable streams.
- `lib_rawinstream.c:lib_rawinstream`, `lib_rawoutstream.c:lib_rawoutstream`, `lib_rawsistream.c:lib_rawsistream`, `lib_rawsostream.c:lib_rawsostream`, `lib_bufferedoutstream.c:lib_bufferedoutstream` - Unbuffered and stack/struct-buffered POSIX file descriptor (`fd`) streams.
- `lib_fileinstream.c:lib_fileinstream_open`, `lib_fileinstream.c:lib_fileinstream_close`, `lib_fileoutstream.c:lib_fileoutstream_open`, `lib_fileoutstream.c:lib_fileoutstream_close` - Kernel VFS `struct file` streams (`file_read`/`file_write`).
- `lib_stdinstream.c:lib_stdinstream`, `lib_stdoutstream.c:lib_stdoutstream`, `lib_stdsistream.c:lib_stdsistream`, `lib_stdsostream.c:lib_stdsostream` - Streams backed by standard `<stdio.h>` `FILE *` handles.
- `lib_nullinstream.c:lib_nullinstream`, `lib_nulloutstream.c:lib_nulloutstream`, `lib_zeroinstream.c:lib_zeroinstream`, `lib_libnoflush.c:lib_noflush`, `lib_libsnoflush.c:lib_snoflush` - Null/EOF sink, zero-byte source, and no-op flush callbacks.
- `lib_lowoutstream.c:lib_lowoutstream`, `lib_lowoutstream.c:g_lowoutstream`, `lib_syslogstream.c:lib_syslogstream`, `lib_syslograwstream.c:lib_syslograwstream_open`, `lib_syslograwstream.c:lib_syslograwstream_close` - Low-level UART (`up_putc`/`up_nputs`) and `syslog`/`nx_syslog` output streams.
- `lib_blkoutstream.c:lib_blkoutstream_open`, `lib_blkoutstream.c:lib_blkoutstream_close`, `lib_mtdoutstream.c:lib_mtdoutstream_open`, `lib_mtdoutstream.c:lib_mtdoutstream_close`, `lib_mtdsostream.c:lib_mtdsostream_open`, `lib_mtdsostream.c:lib_mtdsostream_close` - Block device and MTD flash eraseblock-cached output/seekable streams.
- `lib_base64outstream.c:lib_base64outstream`, `lib_hexdumpstream.c:lib_hexdumpstream`, `lib_lzfcompress.c:lib_lzfoutstream` - Filter output streams performing Base64 encoding, hex dumping, and LZF compression into a downstream `struct lib_outstream_s`.

## Invariants
- Every stream implementation maintains `stream->nget` (total bytes read) or `stream->nput` (total bytes written) monotonically across `getc`/`gets`/`putc`/`puts` operations.
- `lib_memoutstream.c` always preserves space for a trailing NUL terminator (`buflen - 1` writable payload bytes) when `buflen > 0`.

## Side Effects
- Concrete streams perform underlying I/O (`_NX_READ`, `_NX_WRITE`, `_NX_SEEK`, `file_read`, `file_write`, `fgetc`, `fputc`, `up_putc`, `nx_syslog`, block/MTD driver `BREAD`/`BWRITE`/`ERASE`) and dynamic cache allocation (`kmm_malloc`/`kmm_free` in `lib_blkoutstream.c`, `lib_mtdoutstream.c`, `lib_mtdsostream.c`).

## Verification
- Run: `make test`
