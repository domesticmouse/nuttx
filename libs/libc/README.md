# NuttX Standard C Library (`libc`)

## Overview
Internal C library header (`libc.h`), compile-time architecture limit verification (`limits_check.c`), and build rules (`Makefile`, `CMakeLists.txt`, `Kconfig`) including symbol table generation from `libc.csv`, `libm.csv`, and `syscall.csv`, aggregating all user/kernel C library modules.

## Interface
- `[libc.h:libc_data_t]`
- `[libc.h:CONFIG_LIBC_HOMEDIR]`
- `[libc.h:ARCH_LIBCFUN]`
- `[libc.h:UNALIGNED_X]`
- `[libc.h:UNALIGNED]`
- `[libc.h:MISALIGNED]`
- `[libc.h:ALIGNED]`
- `[libc.h:LITTLEBLOCKSIZE]`
- `[libc.h:BIGBLOCKSIZE]`
- `[libc.h:TOO_SMALL]`
- `[libc.h:DETECTNULL]`
- `[libc.h:DETECTCHAR]`
- `[libc.h:DETECTNULL32]`
- `[libc.h:DETECTCHAR32]`
- `[libc.h:UNALIGNED4]`
- `[libc.h:UNALIGNED4_X]`
- `[libc.h:LITTLEBLOCKSIZE4]`
- `[libc.h:BIGBLOCKSIZE4]`
- `[libc.h:TOO_SMALL4]`
- `[libc.h:lib_getfullpath]`
- `[libc.h:lib_mode2oflags]`
- `[libc.h:lib_fwrite]`
- `[libc.h:lib_fwrite_unlocked]`
- `[libc.h:lib_fread_unlocked]`
- `[libc.h:lib_dgets]`
- `[libc.h:lib_fgets]`
- `[libc.h:lib_fgets_unlocked]`
- `[libc.h:lib_flushall]`
- `[libc.h:lib_flushall_unlocked]`
- `[libc.h:lib_fflush]`
- `[libc.h:lib_fflush_unlocked]`
- `[libc.h:lib_rdflush_unlocked]`
- `[libc.h:lib_wrflush_unlocked]`
- `[libc.h:lib_getbase]`
- `[libc.h:lib_skipspace]`
- `[libc.h:lib_isbasedigit]`
- `[libc.h:lib_checkbase]`
- `[libc.h:lib_parse_hostfile]`
- `[libc.h:lib_restoredir]`
- `[libc.h:lib_cxx_initialize]`
- [`aio`](./aio/README.md) - POSIX asynchronous I/O (`<aio.h>`) status retrieval, result extraction, and caller suspension helpers.
- [`assert`](./assert/README.md) - Runtime assertion failure handler (`__assert`) and compiler stack-smashing protector callbacks.
- [`audio`](./audio/README.md) - Allocation, reference counting, and deallocation routines for Audio Pipeline Buffers (`struct ap_buffer_s`).
- [`builtin`](./builtin/README.md) - Lookup and metadata query functions for compile-time registered NuttX built-in applications (`g_builtins`).
- [`ctype`](./ctype/README.md) - Standard C `<ctype.h>` character classification and case conversion functions and lookup table.
- [`dirent`](./dirent/README.md) - POSIX `<dirent.h>` directory stream operations, directory scanning/sorting, and `<ftw.h>` file tree walks.
- [`dlfcn`](./dlfcn/README.md) - POSIX `<dlfcn.h>` dynamic linker interface (`dlopen`, `dlsym`, `dlclose`, `dlerror`, `dladdr`) wrapping `libelf`.
- [`elf`](./elf/README.md) - Runtime ELF shared object loader, symbol resolver, relocation engine, address environment manager, and module registry.
- [`environ`](./environ/README.md) - Task-group environment variable management (`getenv`, `secure_getenv`, `setenv`, `putenv`, `unsetenv`, `clearenv`).
- [`errno`](./errno/README.md) - Thread-local `errno` pointer accessor (`__errno`) backed by TLS with static fallback.
- [`eventfd`](./eventfd/README.md) - C library wrappers (`eventfd_read`, `eventfd_write`) for 64-bit counter I/O on `eventfd` descriptors.
- [`fdt`](./fdt/README.md) - Build configuration and version header (`version_gen.h`) for Flattened Device Tree (`libfdt`) integration.
- [`fixedmath`](./fixedmath/README.md) - 16.16 and 8.8 fixed-point trigonometric (`b16sin`, `b16cos`, `b16atan2`) and square-root routines.
- [`gdbstub`](./gdbstub/README.md) - GDB Remote Serial Protocol (RSP) target stub supporting memory/register access, thread queries, and debugpoints.
- [`grp`](./grp/README.md) - POSIX `<grp.h>` group database lookup, iteration, and supplementary group initialization functions.
- [`hex2bin`](./hex2bin/README.md) - Intel HEX ASCII stream parser and binary memory/stream writer (`hex2bin`, `data2bin`, `hex2mem`, `fhex2mem`).
- [`inttypes`](./inttypes/README.md) - Standard C99 `<inttypes.h>` `intmax_t`/`uintmax_t` arithmetic (`imaxabs`, `imaxdiv`) and string conversions.
- [`libgen`](./libgen/README.md) - POSIX `<libgen.h>` pathname component extraction functions (`basename`, `dirname`).
- [`locale`](./locale/README.md) - POSIX locale management, X/Open message catalogs, GNU `gettext` `.mo` translation, and `iconv` conversion.
- [`lzf`](./lzf/README.md) - LibLZF lossless high-speed data compression (`lzf_compress`) and decompression (`lzf_decompress`).
- [`machine`](./machine/README.md) - Architecture-specific C library routines, atomic helpers, ELF relocation handlers, and `setjmp`/`longjmp`.
- [`misc`](./misc/README.md) - OS mutex primitives (`nxmutex`, `nxrmutex`), circular buffers, bitmaps, IDR trees, backtraces, CRCs, `*at` VFS wrappers, and `fdsan`/`fdcheck`.
- [`net`](./net/README.md) - Network byte-order conversions, IPv4/IPv6/Ethernet/Base64 address formatting, interface enumeration, and routing helpers.
- [`netdb`](./netdb/README.md) - POSIX `<netdb.h>` and `<resolv.h>` host/service/protocol lookups, `/etc/hosts` parser, and DNS client resolver/cache.
- [`obstack`](./obstack/README.md) - GNU-compatible `<obstack.h>` LIFO object stack chunk allocator.
- [`pthread`](./pthread/README.md) - User-space POSIX Threads (`<pthread.h>`) lifecycle, attributes, TLS keys, cancellation, mutexes, condvars, rwlocks, barriers, and spinlocks.
- [`pwd`](./pwd/README.md) - POSIX `<pwd.h>` password database and `/etc/passwd` lookup functions (`getpwnam`, `getpwuid`, `getpwent`).
- [`queue`](./queue/README.md) - Singly and doubly linked queue manipulation functions (`sq_*`, `dq_*`) for `<nuttx/queue.h>`.
- [`regex`](./regex/README.md) - POSIX regular expression compiler and matcher (`regcomp`, `regexec`, `regerror`, `regfree`).
- [`sched`](./sched/README.md) - Scheduler policy/priority helpers, `task_setcancelstate`/`task_setcanceltype`, and clock/CPU-affinity helpers.
- [`search`](./search/README.md) - POSIX `<search.h>` hash table (`hsearch`), binary search tree (`tsearch`), and linear search (`lsearch`, `lfind`) routines.
- [`semaphore`](./semaphore/README.md) - POSIX `<semaphore.h>` counting semaphore initialization, wait, post, and named semaphore wrappers.
- [`signal`](./signal/README.md) - POSIX `<signal.h>` signal set manipulation, `sigaction`/`kill`/`raise`/`sigwait` wrappers, and signal name tables.
- [`spawn`](./spawn/README.md) - POSIX `<spawn.h>` file actions (`posix_spawn_file_actions_*`), spawn attributes (`posix_spawnattr_*`), and `posix_spawnp`.
- [`stdio`](./stdio/README.md) - Standard C `<stdio.h>` buffered file streams (`FILE`), `printf`/`scanf` formatting engines, and file descriptor wrappers.
- [`stdlib`](./stdlib/README.md) - Standard C `<stdlib.h>` numeric conversions, PRNGs, `qsort`/`bsearch`, `atexit`/`abort`/`exit`, PTY helpers, and `system`.
- [`stream`](./stream/README.md) - Abstract input/output stream implementations (`lib_instream_s`, `lib_outstream_s`) for memory, files, buffers, MTD, block devices, LZF, and syslog.
- [`string`](./string/README.md) - Standard C `<string.h>` and `<strings.h>` memory and NUL-terminated string manipulation routines.
- [`symtab`](./symtab/README.md) - Symbol table lookup (`symtab_findbyname`, `symtab_findbyvalue`) and sorting (`symtab_sortbyname`) utilities.
- [`syslog`](./syslog/README.md) - POSIX `<syslog.h>` logging interface (`syslog`, `vsyslog`, `openlog`, `closelog`, `setlogmask`).
- [`termios`](./termios/README.md) - POSIX `<termios.h>` terminal control (`tcgetattr`, `tcsetattr`, `tcdrain`, `tcflush`, `cfgetspeed`, `cfsetspeed`, `cfmakeraw`).
- [`time`](./time/README.md) - Standard C `<time.h>` and POSIX `<sys/time.h>` calendar conversions (`gmtime`, `localtime`, `mktime`, `strftime`, `strptime`), timers, and `clock`/`difftime`.
- [`tls`](./tls/README.md) - Thread-Local Storage (`struct tls_info_s`, `struct task_info_s`) allocation, cleanup stack, and `errno`/argv helpers.
- [`uio`](./uio/README.md) - Scatter/gather vector I/O (`readv`, `writev`, `preadv`, `pwritev`) implementations (`<sys/uio.h>`).
- [`unistd`](./unistd/README.md) - POSIX `<unistd.h>` process, working directory, sleep, pipe, getopt, sysconf/pathconf, credentials, and VFS wrapper functions.
- [`userfs`](./userfs/README.md) - Userspace filesystem (`userfs_run`) server loop forwarding kernel VFS requests over localhost UDP sockets to user callbacks.
- [`uuid`](./uuid/README.md) - DCE 1.1 / RFC 4122 UUID generation, parsing, formatting, comparison, and byte-packing utilities (`<uuid.h>`).
- [`wchar`](./wchar/README.md) - Wide-character (`<wchar.h>`) string manipulation, multibyte conversion (`mbrtowc`, `wcrtomb`), and wide I/O functions.
- [`wctype`](./wctype/README.md) - Wide-character classification and mapping functions (`<wctype.h>`: `iswctype`, `towctrans`, `wctype`, `wctrans`).
- [`wqueue`](./wqueue/README.md) - User-space work queue (`USRWORK`) thread pool, delayed work scheduling (`work_queue`), cancellation, and notification helpers.
- [`zoneinfo`](./zoneinfo/README.md) - Built-in IANA time zone database (`tzromfs`) ROMFS image generation and mounting support.

## Invariants
- Compile-time assertions verify that NuttX `<limits.h>` and `<float.h>` constants (`CHAR_BIT`, `SCHAR_MAX`, `SHRT_MAX`, `LONG_MAX`, `LLONG_MAX`, `UPTR_MAX`, `WCHAR_MAX`, and `FLT_*`/`DBL_*`/`LDBL_*` macros) match compiler predefined macros (`__CHAR_BIT__`, etc.) when present `[limits_check.c:static_assert_equal]`.

## Side Effects
- Generates `exec_symtab.c` and/or `elf_sys_symtab.c` at build time using host tool `mksymtab` from sorted `libc.csv`, `libm.csv`, and `syscall.csv` when `CONFIG_EXECFUNCS_SYSTEM_SYMTAB` or `CONFIG_LIBC_ELF_SYSTEM_SYMTAB` is enabled `[Makefile:exec_symtab.c]`.

## Verification
- Run: `make test`
