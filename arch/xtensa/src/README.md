# src (`nuttx/arch/xtensa/src`)

## Overview
Architectural grouping for `nuttx/arch/xtensa/src`, coordinating 4 component subdirectories (`common`, `esp32`, `esp32s2`, `esp32s3`).

## Subdirectories & Boundaries
- `common`: [./common/README.md](./common/README.md) - Hardware abstraction and architecture package for `common` under `nuttx/arch/xtensa/src/common`, providing 7 header file(s) and 42 source file(s) (including `mpu.h`, `xtensa.h`, `xtensa_asm_utils.h`, `xtensa_attr.h`).
- `esp32`: [./esp32/README.md](./esp32/README.md) - Hardware abstraction and architecture package for `esp32` (ESP32 Configuration Options; ESP32 Peripheral Selection) under `nuttx/arch/xtensa/src/esp32`, providing 41 header file(s) and 55 source file(s) (including `chip.h`, `chip_macros.h`, `chip_memory.h`, `esp32_aes.h`).
- `esp32s2`: [./esp32s2/README.md](./esp32s2/README.md) - Hardware abstraction and architecture package for `esp32s2` (ESP32-S2 Configuration Options; Cache Configuration) under `nuttx/arch/xtensa/src/esp32s2`, providing 24 header file(s) and 32 source file(s) (including `chip.h`, `chip_macros.h`, `chip_memory.h`, `esp32s2_config.h`).
- `esp32s3`: [./esp32s3/README.md](./esp32s3/README.md) - Hardware abstraction and architecture package for `esp32s3` (ESP32-S3 Configuration Options; Cache configuration) under `nuttx/arch/xtensa/src/esp32s3`, providing 46 header file(s) and 62 source file(s) (including `chip.h`, `chip_macros.h`, `chip_memory.h`, `esp32s3_addrenv.h`).

## Interface
- `[Makefile:CHIP_CSRCS]`
- `[Makefile:CMN_CSRCS]`
- `[Makefile:HEAD_ASRC]`
- `[Makefile:CSRCS]`
- `[Makefile:ASRCS]`
- [./common/README.md](./common/README.md)
- [./esp32/README.md](./esp32/README.md)
- [./esp32s2/README.md](./esp32s2/README.md)
- [./esp32s3/README.md](./esp32s3/README.md)

## Invariants
- `[xtensa.h:#error]` Compile-time guard: CONFIG_IDLETHREAD_STACKSIZE is not defined
- `[xtensa_asm_utils.h:#error]` Compile-time guard: Unrecognized XCHAL_NUM_AREGS
- `[xtensa_timer.h:#error]` Compile-time guard: This Xtensa configuration is unsupported, it has no timers.
- `[xtensa_addrenv_kstack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[xtensa_cpenable.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[xtensa_cpuint.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[xtensa.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[xtensa.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[xtensa.h:modifyreg32]` Performs atomic read-modify-write updates on 32-bit MMIO registers
- `[xtensa_counter.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[crt0.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)
- `[xtensa_backtrace.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)

## Verification
- Run: `make test`
