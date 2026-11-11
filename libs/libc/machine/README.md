# Architecture-Specific Libc Support (`libs/libc/machine`)

## Overview
Provides generic software fallback implementations of 8/16/32/64-bit C11 `__atomic_*` and GCC `__sync_*` built-ins (synchronized via IRQ masking, hardware spinlocks, or SMP spinlocks), KASan-instrumented wrappers around architecture-optimized string/memory routines, and subdirectories for target CPU architectures.

## Interface
- `arch_atomic.h:STORE`, `arch_atomic.h:LOAD`, `arch_atomic.h:EXCHANGE`, `arch_atomic.h:CMP_EXCHANGE`, `arch_atomic.h:FLAG_TEST_AND_SET`, `arch_atomic.h:FETCH_ADD`, `arch_atomic.h:FETCH_SUB`, `arch_atomic.h:FETCH_AND`, `arch_atomic.h:FETCH_OR`, `arch_atomic.h:FETCH_XOR`, `arch_atomic.h:SYNC_ADD_FETCH`, `arch_atomic.h:SYNC_SUB_FETCH`, `arch_atomic.h:SYNC_OR_FETCH`, `arch_atomic.h:SYNC_AND_FETCH`, `arch_atomic.h:SYNC_XOR_FETCH`, `arch_atomic.h:SYNC_NAND_FETCH`, `arch_atomic.h:SYNC_BOOL_CMP_SWAP`, `arch_atomic.h:SYNC_VAL_CMP_SWAP` - Code-generation macros defining weak atomic functions guarded by `atomic_lock`/`atomic_unlock`.
- `arch_atomic.c:__atomic_store_1`, `arch_atomic.c:__atomic_store_2`, `arch_atomic.c:__atomic_store_4`, `arch_atomic.c:atomic_store_4`, `arch_atomic.c:__atomic_load_1`, `arch_atomic.c:__atomic_load_2`, `arch_atomic.c:__atomic_load_4`, `arch_atomic.c:atomic_load_4`, `arch_atomic.c:__atomic_exchange_1`, `arch_atomic.c:__atomic_exchange_2`, `arch_atomic.c:__atomic_exchange_4`, `arch_atomic.c:atomic_exchange_4`, `arch_atomic.c:__atomic_compare_exchange_1`, `arch_atomic.c:__atomic_compare_exchange_2`, `arch_atomic.c:__atomic_compare_exchange_4`, `arch_atomic.c:atomic_compare_exchange_4`, `arch_atomic.c:__atomic_flags_test_and_set_1`, `arch_atomic.c:__atomic_flags_test_and_set_2`, `arch_atomic.c:__atomic_flags_test_and_set_4`, `arch_atomic.c:atomic_flags_test_and_set_4`, `arch_atomic.c:__atomic_fetch_add_1`..`4`, `arch_atomic.c:__atomic_fetch_sub_1`..`4`, `arch_atomic.c:__atomic_fetch_and_1`..`4`, `arch_atomic.c:__atomic_fetch_or_1`..`4`, `arch_atomic.c:__atomic_fetch_xor_1`..`4`, `arch_atomic.c:__sync_synchronize` - Weak 1/2/4-byte atomic and `__sync_*` functions guarded by `CONFIG_LIBC_ATOMIC_HWSPINLOCK` or `CONFIG_LIBC_ATOMIC_IRQ`.
- `arch_atomic64.c:__atomic_store_8`, `arch_atomic64.c:__atomic_load_8`, `arch_atomic64.c:__atomic_exchange_8`, `arch_atomic64.c:__atomic_compare_exchange_8`, `arch_atomic64.c:__atomic_flags_test_and_set_8`, `arch_atomic64.c:__atomic_fetch_add_8`, `arch_atomic64.c:__atomic_fetch_sub_8`, `arch_atomic64.c:__atomic_fetch_and_8`, `arch_atomic64.c:__atomic_fetch_or_8`, `arch_atomic64.c:__atomic_fetch_xor_8` - Weak 8-byte (64-bit) atomic and `__sync_*` functions serialized via `g_atomic_lock` (`spin_lock_irqsave`).
- `arch_libc.c:memchr`, `arch_libc.c:memcpy`, `arch_libc.c:memcmp`, `arch_libc.c:memmove`, `arch_libc.c:memset`, `arch_libc.c:strcmp`, `arch_libc.c:strcpy`, `arch_libc.c:strlen`, `arch_libc.c:strncpy`, `arch_libc.c:strchr`, `arch_libc.c:strchrnul`, `arch_libc.c:strncmp`, `arch_libc.c:strnlen`, `arch_libc.c:strrchr` - KASan-instrumented (`CONFIG_MM_KASAN_INSTRUMENT`) wrapper functions delegating to `ARCH_LIBCFUN(*)`.
- `./arm/README.md` - 32-bit ARM EABI runtime helpers, CRC32, unwind lookup, and architecture profiles.
- `./arm64/README.md` - 64-bit AArch64 ELF relocation, `ucontext_t`, and profiling support.
- `./mips/README.md` - 32-bit MIPS ELF relocation support.
- `./risc-v/README.md` - RISC-V (RV32/RV64) assembly macros and ELF relocation support.
- `./sim/README.md` - Host simulator 32-bit and 64-bit ELF relocation support.
- `./sparc/README.md` - 32-bit SPARC ELF relocation support.
- `./tricore/README.md` - Infineon TriCore hardware atomic operations.
- `./x86/README.md` - 32-bit x86 ELF relocation support.
- `./x86_64/README.md` - 64-bit x86_64 cache definitions and ELF relocation support.
- `./xtensa/README.md` - Xtensa assembly macros, profiling, and ELF relocation support.

## Invariants
- `arch_atomic.c:atomic_lock` and `arch_atomic64.c:atomic_lock` preserve interrupt state across every atomic memory access (`up_irq_save`, `hwspin_lock_irqsave`, or `spin_lock_irqsave`).
- `arch_libc.c` wrappers perform KASan read/write range checks (`__asan_loadN`, `__asan_storeN`) prior to or immediately after invoking `ARCH_LIBCFUN(*)` when `CONFIG_MM_KASAN_INSTRUMENT` is enabled.

## Side Effects
- `arch_atomic.c` and `arch_atomic64.c` mask local interrupts and acquire hardware/SMP spinlocks (`g_atomic_hwspinlock` or `g_atomic_lock`) while mutating target atomic variables.
- `arch_libc.c` mutates destination buffers (`memcpy`, `memmove`, `memset`, `strcpy`, `strncpy`) and triggers KASan fault reporting via `__asan_loadN`/`__asan_storeN` on invalid memory accesses.

## Verification
- Run: `make test`
