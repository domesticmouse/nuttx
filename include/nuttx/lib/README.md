# Core C Library & Runtime Support (`include/nuttx/lib`)

## Overview
Provides internal and portable C library support headers for NuttX, including built-in application registry lookup (`builtin.h`), shared ELF module management (`elf.h`), floating-point limits and math declarations (`float.h`, `math.h`), context-aware kernel/user memory allocation wrappers and temporary path buffers (`lib.h`), 32/64-bit integer arithmetic and bit-scan helpers (`math32.h`), signal-aware non-local jumps (`setjmp.h`), variable argument macros (`stdarg.h`), C23 bit and byte utilities (`stdbit.h`), and PRNG/checksum utilities (`xorshift128.h`, `xorsum.h`).

## Interface
- `builtin.h:struct builtin_s`, `builtin.h:g_builtins`, `builtin.h:g_builtin_count`, `builtin.h:builtin_isavail`, `builtin.h:builtin_getname`, `builtin.h:builtin_for_index`, `builtin.h:builtin_getuid`, `builtin.h:builtin_getgid`, `builtin.h:builtin_getmode`
- `elf.h:struct module_s`, `elf.h:struct mod_info_s`, `elf.h:struct mod_loadinfo_s`, `elf.h:libelf_insert`, `elf.h:libelf_getsymbol`, `elf.h:libelf_remove`, `elf.h:libelf_removeall`, `elf.h:libelf_registry_find`, `elf.h:libelf_registry_foreach`, `elf.h:libelf_findsymbol`
- `lib.h:lib_malloc`, `lib.h:lib_calloc`, `lib.h:lib_zalloc`, `lib.h:lib_realloc`, `lib.h:lib_memalign`, `lib.h:lib_free`, `lib.h:lib_get_streams`, `lib.h:lib_get_stream`, `lib.h:lib_get_tempbuffer`, `lib.h:lib_put_tempbuffer`, `lib.h:lib_get_pathbuffer`, `lib.h:lib_put_pathbuffer`, `lib.h:lib_realpath`, `lib.h:nrand`
- `math32.h:struct int64_s`, `math32.h:struct uint64_s`, `math32.h:invdiv_param32_t`, `math32.h:invdiv_param64_t`, `math32.h:div_round_up`, `math32.h:div_round_closest`, `math32.h:FLS`, `math32.h:LOG2_CEIL`, `math32.h:LOG2_FLOOR`, `math32.h:uadd64`, `math32.h:usub64`, `math32.h:umul32`, `math32.h:umul64`
- `float.h:FLT_RADIX`, `float.h:FLT_MANT_DIG`, `float.h:DBL_MANT_DIG`, `float.h:LDBL_MANT_DIG`
- `math.h:INFINITY`, `math.h:NAN`, `math.h:isnan`, `math.h:isinf`, `math.h:isfinite`, `math.h:fpclassify`
- `setjmp.h:struct sigsetjmp_buf_s`, `setjmp.h:sigjmp_buf`, `setjmp.h:sigsetjmp`, `setjmp.h:siglongjmp`
- `stdbit.h:stdc_leading_zeros_ui`, `stdbit.h:stdc_trailing_zeros_ui`, `stdbit.h:stdc_has_single_bit`, `stdbit.h:stdc_bit_width`, `stdbit.h:stdc_bit_floor`, `stdbit.h:stdc_bit_ceil`
- `xorshift128.h:struct xorshift128_state_s`, `xorshift128.h:XORSHIFT128_INITIALIZER`, `xorshift128.h:xorshift128`
- `xorsum.h:xorsum16`

## Invariants
- `lib.h:lib_malloc` and related allocation macros dispatch to `kmm_*` when `__KERNEL__` is defined and to standard user-space `malloc`/`free` otherwise.
- `xorshift128.h:struct xorshift128_state_s` must not be initialized to all zeros; `xorshift128.h:XORSHIFT128_INITIALIZER` provides a valid non-zero seed state.
- `stdbit.h` generic implementations require compiler support for `CONFIG_HAVE_BUILTIN_CLZ`, `CONFIG_HAVE_BUILTIN_CTZ`, `CONFIG_HAVE_BUILTIN_POPCOUNT`, and `CONFIG_HAVE_BUILTIN_POPCOUNTLL`.

## Side Effects
- `lib.h:lib_malloc`, `lib.h:lib_free`, and `lib.h:lib_get_tempbuffer` allocate and release memory from the kernel or user heap.
- `elf.h:libelf_insert` and `elf.h:libelf_remove` load ELF sections into memory, execute module initializers/uninitializers, and mutate the module registry list.
- `setjmp.h:sigsetjmp` and `setjmp.h:siglongjmp` query and restore the calling thread's signal mask via `sigprocmask` when `savemask` is non-zero.

## Verification
- Run: `make test`
