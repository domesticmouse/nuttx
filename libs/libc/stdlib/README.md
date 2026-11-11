# Standard Library Utilities (`libs/libc/stdlib`)

## Overview
Implements ISO C, POSIX, and BSD `<stdlib.h>` and `<pty.h>` utilities, including string-to-number conversions (`strto*`, `ato*`, `itoa`), pseudo-random number generators (`rand`, `rand48`, `arc4random`), sorting and binary search (`qsort`, `bsearch`), aligned memory allocation wrappers, process termination and exit hooks (`exit`, `atexit`, `abort`), multibyte/wide-character conversions, temporary file/directory creation (`mkstemp`, `mkdtemp`), canonical path resolution (`realpath`), and pseudo-terminal management (`openpty`, `forkpty`, `ptsname`).

## Interface
- `lib_atoi.c:atoi`, `lib_atol.c:atol`, `lib_atoll.c:atoll`, `lib_atof.c:atof`, `lib_itoa.c:itoa`, `lib_checkbase.c:lib_checkbase` - Basic integer/floating-point string conversions and radix prefix detection (`0x`, `0b`, `0`).
- `lib_strtol.c:strtol`, `lib_strtoll.c:strtoll`, `lib_strtoul.c:strtoul`, `lib_strtoull.c:strtoull`, `lib_strtold.c:strtof`, `lib_strtold.c:strtod`, `lib_strtold.c:strtold` - Full-featured string-to-integer and decimal/hexadecimal string-to-floating-point parsers with overflow clamping (`ERANGE`).
- `lib_abs.c:abs`, `lib_labs.c:labs`, `lib_llabs.c:llabs`, `lib_div.c:div`, `lib_ldiv.c:ldiv`, `lib_lldiv.c:lldiv` - Integer absolute value and quotient/remainder division functions.
- `lib_rand.c:rand`, `lib_rand.c:random`, `lib_rand.c:srandom`, `lib_srand.c:srand`, `lib_srand.c:nrand`, `lib_srand.c:rand_r`, `lib_rand48.c:drand48`, `lib_rand48.c:erand48`, `lib_rand48.c:lrand48`, `lib_rand48.c:nrand48`, `lib_rand48.c:mrand48`, `lib_rand48.c:jrand48`, `lib_rand48.c:srand48`, `lib_rand48.c:seed48`, `lib_rand48.c:lcong48`, `lib_arc4random.c:arc4random`, `lib_arc4random.c:arc4random_buf` - Pseudo-random and entropy-backed random number generators.
- `lib_bsearch.c:bsearch`, `lib_qsort.c:qsort` - Binary search and Bentley-McIlroy quicksort over arbitrary arrays.
- `lib_aligned_alloc.c:aligned_alloc`, `lib_posix_memalign.c:posix_memalign`, `lib_valloc.c:valloc`, `lib_reallocarray.c:reallocarray`, `lib_malloc_usable_size.c:malloc_usable_size` - Aligned allocation, overflow-checked array reallocation, and allocation size query wrappers.
- `lib_atexit.c:atexit`, `lib_atexit.c:at_quick_exit`, `lib_atexit.c:on_exit`, `lib_atexit.c:__cxa_atexit`, `lib_atexit.c:atexit_register`, `lib_atexit.c:atexit_call_exitfuncs`, `lib_exit.c:exit`, `lib_exit.c:quick_exit`, `lib_exit.c:_Exit`, `lib_abort.c:abort` - Process termination, registered exit handler execution, and abnormal termination (`raise(SIGABRT)`).
- `lib_mblen.c:mblen`, `lib_mbtowc.c:mbtowc`, `lib_wctomb.c:wctomb`, `lib_mbstowcs.c:mbstowcs`, `lib_wcstombs.c:wcstombs` - Stateless/stateful multibyte and wide-character conversion wrappers.
- `lib_mktemp.c:mktemp`, `lib_mkstemp.c:mkstemp`, `lib_mkstemp.c:mkstemps`, `lib_mkstemp.c:mkostemp`, `lib_mkstemp.c:mkostemps`, `lib_mkdtemp.c:mkdtemp`, `lib_realpath.c:realpath`, `lib_realpath.c:lib_realpath` - Unique temporary file/directory creation and symlink-aware canonical path resolution (`CONFIG_FS_LINKS`).
- `lib_openpty.c:posix_openpt`, `lib_openpty.c:openpty`, `lib_forkpty.c:forkpty`, `lib_grantpt.c:grantpt`, `lib_unlockpt.c:unlockpt`, `lib_ptsname.c:ptsname`, `lib_ptsnamer.c:ptsname_r` - Pseudo-terminal master/slave creation, ioctl unlocking (`TIOCSPTLCK`), and slave device path queries (`TIOCGPTN`).
- `lib_getprogname.c:getprogname`, `lib_getloadavg.c:getloadavg` - Query current task program name (`argv[0]`) and system CPU load averages (`clock_cpuload`).

## Invariants
- `lib_posix_memalign.c:posix_memalign` requires `align` to be a power of two and a multiple of `sizeof(void *)`, returning `EINVAL` otherwise.
- `lib_reallocarray.c:reallocarray` rejects `(nmemb * size)` multiplications that overflow `size_t`, returning `NULL` with `errno = ENOMEM`.
- `lib_bsearch.c:bsearch` asserts `DEBUGASSERT(key != NULL)`, `DEBUGASSERT(base != NULL || nel == 0)`, and `DEBUGASSERT(compar != NULL)`.

## Side Effects
- `lib_exit.c:exit` and `lib_exit.c:quick_exit` run registered `atexit`/`__cxa_atexit` destructors (`atexit_call_exitfuncs`), run TLS destructors (`tls_destruct`, `task_tls_destruct`), flush streams, and terminate the process via `_exit`.
- `lib_arc4random.c:arc4random_buf`, `lib_mktemp.c`, `lib_mkstemp.c`, `lib_mkdtemp.c`, `lib_realpath.c`, and `lib_openpty.c` perform filesystem/device I/O (`open`, `read`, `mkdir`, `stat`, `lstat`, `readlink`, `ioctl`).
- `lib_srand.c` and `lib_rand48.c` mutate module-static PRNG state (`g_seed`, `__rand48_seed`, `__rand48_mult`, `__rand48_add`).

## Verification
- Run: `make test`
