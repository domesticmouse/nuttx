# Standard Buffered I/O (`libs/libc/stdio`)

## Overview
Implements ISO C and POSIX `<stdio.h>` and `<stdio_ext.h>` buffered stream management, formatted output (`printf` family), formatted input (`scanf` family), byte and wide-character stream I/O, custom cookie and memory streams (`fopencookie`, `fmemopen`, `open_memstream`), process pipes (`popen`/`pclose`), temporary file generation, and stream locking.

## Interface
- `lib_fopen.c:fopen`, `lib_fopen.c:fdopen`, `lib_fopen.c:lib_mode2oflags`, `lib_freopen.c:freopen`, `lib_fclose.c:fclose` - Open, re-open, and close `FILE` streams and translate mode strings (`r`, `w`, `a`, `+`, `b`, `x`, `e`) to `O_*` flags.
- `lib_fopencookie.c:fopencookie`, `lib_fmemopen.c:fmemopen`, `lib_open_memstream.c:open_memstream` - Create custom callback-backed and memory-buffer-backed `FILE` streams.
- `lib_fread.c:fread`, `lib_fread.c:fread_unlocked`, `lib_libfread_unlocked.c:lib_fread_unlocked`, `lib_fwrite.c:fwrite`, `lib_fwrite.c:fwrite_unlocked`, `lib_libfwrite.c:lib_fwrite`, `lib_libfwrite.c:lib_fwrite_unlocked` - Buffered binary read and write operations on `FILE` streams.
- `lib_fgetc.c:fgetc`, `lib_fgetc.c:fgetc_unlocked`, `lib_getc.c:getc`, `lib_getc.c:getc_unlocked`, `lib_getchar.c:getchar`, `lib_getchar.c:getchar_unlocked`, `lib_fgets.c:fgets`, `lib_fgets.c:fgets_unlocked`, `lib_libfgets.c:lib_fgets`, `lib_libfgets.c:lib_fgets_unlocked`, `lib_libdgets.c:lib_dgets`, `lib_gets.c:gets`, `lib_gets_s.c:gets_s`, `lib_getdelim.c:getdelim`, `lib_getdelim.c:getline`, `lib_ungetc.c:ungetc` - Character and line input functions.
- `lib_fputc.c:fputc`, `lib_fputc.c:fputc_unlocked`, `lib_putc.c:putc`, `lib_putc.c:putc_unlocked`, `lib_putchar.c:putchar`, `lib_putchar.c:putchar_unlocked`, `lib_fputs.c:fputs`, `lib_fputs.c:fputs_unlocked`, `lib_puts.c:puts` - Character and string output functions.
- `lib_fgetwc.c:fgetwc`, `lib_fgetwc.c:fgetwc_unlocked`, `lib_getwc.c:getwc`, `lib_fputwc.c:fputwc`, `lib_fputwc.c:fputwc_unlocked`, `lib_putwc.c:putwc`, `lib_putwc.c:putwc_unlocked`, `lib_putwchar.c:putwchar`, `lib_putwchar.c:putwchar_unlocked`, `lib_fputws.c:fputws`, `lib_fputws.c:fputws_unlocked`, `lib_ungetwc.c:ungetwc`, `lib_ungetwc.c:ungetwc_unlocked` - Wide-character stream I/O functions.
- `lib_printf.c:printf`, `lib_vprintf.c:vprintf`, `lib_fprintf.c:fprintf`, `lib_vfprintf.c:vfprintf`, `lib_sprintf.c:sprintf`, `lib_vsprintf.c:vsprintf`, `lib_snprintf.c:snprintf`, `lib_vsnprintf.c:vsnprintf`, `lib_asprintf.c:asprintf`, `lib_asprintf.c:nx_asprintf`, `lib_vasprintf.c:vasprintf`, `lib_vasprintf.c:nx_vasprintf`, `lib_dprintf.c:dprintf`, `lib_vdprintf.c:vdprintf` - Formatted output functions delegating to `lib_vsprintf`.
- `lib_scanf.c:scanf`, `lib_vscanf.c:vscanf`, `lib_fscanf.c:fscanf`, `lib_vfscanf.c:vfscanf`, `lib_sscanf.c:sscanf`, `lib_vsscanf.c:vsscanf` - Formatted input functions delegating to `lib_vscanf`.
- `lib_fseek.c:fseek`, `lib_fseeko.c:fseeko`, `lib_ftell.c:ftell`, `lib_ftello.c:ftello`, `lib_rewind.c:rewind`, `lib_fgetpos.c:fgetpos`, `lib_fsetpos.c:fsetpos` - Stream positioning and offset query functions.
- `lib_fflush.c:fflush`, `lib_fflush.c:fflush_unlocked`, `lib_libfflush.c:lib_fflush`, `lib_libfflush.c:lib_fflush_unlocked`, `lib_libflushall.c:lib_flushall`, `lib_libflushall.c:lib_flushall_unlocked`, `lib_rdflush_unlocked.c:lib_rdflush_unlocked`, `lib_wrflush_unlocked.c:lib_wrflush_unlocked` - Read/write buffer flushing routines.
- `lib_setbuf.c:setbuf`, `lib_setbuffer.c:setbuffer`, `lib_setvbuf.c:setvbuf` - Configure stream buffering mode (`_IOFBF`, `_IOLBF`, `_IONBF`) and buffer storage (`CONFIG_STDIO_DISABLE_BUFFERING`).
- `lib_feof.c:feof`, `lib_ferror.c:ferror`, `lib_clearerr.c:clearerr`, `lib_clearerr.c:clearerr_unlocked`, `lib_fileno.c:fileno`, `lib_perror.c:perror`, `lib_ctermid.c:ctermid` - Stream status, underlying descriptor, error reporting, and controlling terminal path queries.
- `lib_libfilelock.c:flockfile`, `lib_libfilelock.c:ftrylockfile`, `lib_libfilelock.c:funlockfile`, `lib_libgetstreams.c:lib_get_streams`, `lib_libgetstreams.c:lib_get_stream` - Recursive stream mutex locking (`rmutex_t`) and task-group stream list access.
- `lib_stdio_ext.c:__fbufsize`, `lib_stdio_ext.c:__fpending`, `lib_stdio_ext.c:__freading`, `lib_stdio_ext.c:__fwriting`, `lib_stdio_ext.c:__freadable`, `lib_stdio_ext.c:__fwritable`, `lib_stdio_ext.c:__flbf`, `lib_stdio_ext.c:__fpurge`, `lib_stdio_ext.c:__freadahead`, `lib_stdio_ext.c:__freadptr`, `lib_stdio_ext.c:__freadptrinc`, `lib_stdio_ext.c:__fseterr`, `lib_stdio_ext.c:__fsetlocking`, `lib_stdio_ext.c:_flushlbf` - Solaris/glibc `<stdio_ext.h>` stream introspection and buffer control extensions.
- `lib_popen.c:popen`, `lib_popen.c:pclose`, `lib_remove.c:remove`, `lib_renameat.c:renameat`, `lib_tmpfile.c:tmpfile`, `lib_tmpnam.c:tmpnam`, `lib_tempnam.c:tempnam` - Process pipe streams, file removal/renaming, and temporary file creation.

## Invariants
- Thread-safe stream functions acquire and release the stream's recursive lock via `flockfile`/`funlockfile` unless `FSETLOCKING_BYCALLER` is set or the `*_unlocked` variant is called directly.
- `lib_setvbuf.c:setvbuf` must only be called before any I/O is performed on `stream` (`stream->fs_bufpos == stream->fs_bufstart`), returning `EBADF` if the stream buffer is already in active use.
- `lib_vasprintf.c:vasprintf` and `lib_vasprintf.c:nx_vasprintf` perform a two-pass formatting calculation (`lib_nulloutstream` followed by `lib_memoutstream`) and assert `DEBUGASSERT(nbytes < 0 || nbytes == nulloutstream.nput)`.

## Side Effects
- Performs file descriptor I/O (`open`, `read`, `write`, `lseek`, `close`), file system mutations (`unlink`, `rmdir`, `rename`), FDSAN tag exchanges (`android_fdsan_exchange_owner_tag` when `CONFIG_FDSAN` is enabled), and dynamic memory allocation (`lib_malloc`/`lib_realloc`/`lib_free`).
- Mutates task-group `struct streamlist` linked lists (`sl_head`, `sl_tail`) protected by `sl_lock`, and updates thread `errno` on I/O or allocation failure.

## Verification
- Run: `make test`
