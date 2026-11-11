# ARM32 Machine Support (`libs/libc/machine/arm`)

## Overview
Provides common 32-bit ARM EABI runtime support functions (`__aeabi_*` memory operations, `__aeabi_atexit`), hardware-accelerated ACLE CRC32 calculations, exception unwind table lookup (`__gnu_Unwind_Find_exidx`), GreenHills toolchain dummy symbols, and profile-specific subdirectories for ARMv4/v5 through ARMv8-M/R.

## Interface
- `aeabi_memclr.c:__aeabi_memclr` - Weak EABI wrapper clearing `n` bytes at `s` via `memset`.
- `aeabi_memclr4.c:__aeabi_memclr4` - Weak EABI 4-byte aligned memory clear wrapper.
- `aeabi_memclr8.c:__aeabi_memclr8` - Weak EABI 8-byte aligned memory clear wrapper.
- `aeabi_memcpy.c:__aeabi_memcpy` - Weak EABI memory copy wrapper calling `memcpy`.
- `aeabi_memcpy4.c:__aeabi_memcpy4` - Weak EABI 4-byte aligned memory copy wrapper.
- `aeabi_memcpy8.c:__aeabi_memcpy8` - Weak EABI 8-byte aligned memory copy wrapper.
- `aeabi_memmove.c:__aeabi_memmove` - Weak EABI overlapping memory move wrapper calling `memmove`.
- `aeabi_memmove4.c:__aeabi_memmove4` - Weak EABI 4-byte aligned memory move wrapper.
- `aeabi_memmove8.c:__aeabi_memmove8` - Weak EABI 8-byte aligned memory move wrapper.
- `aeabi_memset.c:__aeabi_memset` - Weak EABI memory fill wrapper translating `(s, n, c)` argument order to `memset(s, c, n)`.
- `aeabi_memset4.c:__aeabi_memset4` - Weak EABI 4-byte aligned memory fill wrapper.
- `aeabi_memset8.c:__aeabi_memset8` - Weak EABI 8-byte aligned memory fill wrapper.
- `arch_atexit.c:__aeabi_atexit` - Registers C++ static object destructors via `atexit_register(ATTYPE_CXA, ...)`.
- `arch_crc32.c:crc32part` - Computes IEEE 802.3 CRC32 using ARM ACLE hardware instructions (`__crc32d`, `__crc32w`, `__crc32h`, `__crc32b`).
- `arch_crc32.c:crc32part_c` - Computes Castagnoli CRC32C using ARM ACLE hardware instructions (`__crc32cd`, `__crc32cw`, `__crc32ch`, `__crc32cb`).
- `arch_dummy.c:__gh_long_long_printf`, `arch_dummy.c:__gh_float_printf`, `arch_dummy.c:__gh_fputs_stdout`, `arch_dummy.c:__gh_set_errno` - No-op stub functions satisfying GreenHills `libmath` link dependencies.
- `arch_unwind_find_exidx.c:up_init_exidx` - Initializes the dynamically loaded ELF `.ARM.exidx` table bounds (`__exidx_start_elf`, `__exidx_end_elf`).
- `arch_unwind_find_exidx.c:__gnu_Unwind_Find_exidx` - Returns the `.ARM.exidx` exception index table and entry count for either flash (`return_address < 0x20000000`) or RAM-loaded ELF modules.
- `./arm/README.md` - Classic ARM (ARMv4/ARMv5) ELF header validation and relocation.
- `./armv6-m/README.md` - ARMv6-M ELF header validation and Thumb relocation.
- `./armv7-a/README.md` - ARMv7-A ACLE compatibility, assembly string routines, and ELF relocation.
- `./armv7-m/README.md` - ARMv7-M ACLE compatibility, Thumb-2 string routines, and ELF relocation.
- `./armv7-r/README.md` - ARMv7-R ACLE compatibility, assembly string routines, and ELF relocation.
- `./armv8-m/README.md` - ARMv8-M ACLE compatibility, Thumb-2 string routines, and ELF relocation.
- `./armv8-r/README.md` - ARMv8-R ACLE compatibility, assembly string routines, and ELF relocation.

## Invariants
- `aeabi_memset.c:__aeabi_memset`, `aeabi_memset4.c:__aeabi_memset4`, `aeabi_memset8.c:__aeabi_memset8` must swap the second and third parameters (`n` and `c`) relative to standard ISO C `memset`.
- `arch_unwind_find_exidx.c:__gnu_Unwind_Find_exidx` assumes the base firmware executes below `0x20000000` (flash) and dynamically loaded ELF modules execute at or above `0x20000000` (RAM).

## Side Effects
- `aeabi_memclr.c:__aeabi_memclr`, `aeabi_memcpy.c:__aeabi_memcpy`, `aeabi_memmove.c:__aeabi_memmove`, `aeabi_memset.c:__aeabi_memset` (and 4/8-byte variants) mutate the destination buffer in memory.
- `arch_atexit.c:__aeabi_atexit` mutates the process/task exit function table via `atexit_register`.
- `arch_unwind_find_exidx.c:up_init_exidx` mutates module-static pointers `__exidx_start_elf` and `__exidx_end_elf`.

## Verification
- Run: `make test`
