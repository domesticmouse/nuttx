# xtensa (`nuttx/arch/xtensa`)

## Overview
Architectural grouping for `nuttx/arch/xtensa`, coordinating 2 component subdirectories (`include`, `src`).

## Subdirectories & Boundaries
- `include`: [./include/README.md](./include/README.md) - Hardware abstraction and architecture package for `include` under `nuttx/arch/xtensa/include`, providing 11 header file(s) and 0 source file(s) (including `arch.h`, `elf.h`, `inttypes.h`, `irq.h`).
- `src`: [./src/README.md](./src/README.md) - Architectural grouping for `nuttx/arch/xtensa/src`, coordinating 4 component subdirectories (`common`, `esp32`, `esp32s2`, `esp32s3`).

## Interface
- `[Kconfig:CONFIG_ARCH_CHIP_ESP32]`
- `[Kconfig:CONFIG_ARCH_CHIP_ESP32S2]`
- `[Kconfig:CONFIG_ARCH_CHIP_ESP32S3]`
- `[Kconfig:CONFIG_ARCH_CHIP_XTENSA_CUSTOM]`
- `[Kconfig:CONFIG_XTENSA_HAVE_ICACHE]`
- `[Kconfig:CONFIG_XTENSA_HAVE_DCACHE]`
- `[Kconfig:CONFIG_XTENSA_HAVE_ICACHE_LOCK]`
- `[Kconfig:CONFIG_XTENSA_HAVE_DCACHE_LOCK]`
- [./include/README.md](./include/README.md)
- [./src/README.md](./src/README.md)

## Invariants
- `[irq.h:#error]` Compile-time guard: Unknown XTENSA architecture
- `[irq.h:DEBUGASSERT]` Enforces runtime precondition assertions in inline/macro helpers
- `[xtensa.h:#error]` Compile-time guard: CONFIG_IDLETHREAD_STACKSIZE is not defined
- `[xtensa_asm_utils.h:#error]` Compile-time guard: Unrecognized XCHAL_NUM_AREGS
- `[xtensa_timer.h:#error]` Compile-time guard: This Xtensa configuration is unsupported, it has no timers.
- `[xtensa_addrenv_kstack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[irq.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[syscall.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[xtensa.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[xtensa.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[xtensa.h:modifyreg32]` Performs atomic read-modify-write updates on 32-bit MMIO registers
- `[xtensa_counter.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations

## Verification
- Run: `make test`
