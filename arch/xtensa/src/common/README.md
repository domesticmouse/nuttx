# common (`nuttx/arch/xtensa/src/common`)

## Overview
Hardware abstraction and architecture package for `common` under `nuttx/arch/xtensa/src/common`, providing 7 header file(s) and 42 source file(s) (including `mpu.h`, `xtensa.h`, `xtensa_asm_utils.h`, `xtensa_attr.h`).

## Subdirectories & Boundaries
- `espressif`: [./espressif/README.md](./espressif/README.md) - Hardware abstraction and architecture package for `espressif` (Espressif Log Level; Interrupt Configuration) under `nuttx/arch/xtensa/src/common/espressif`, providing 34 header file(s) and 38 source file(s) (including `esp_adc.h`, `esp_aes.h`, `esp_dedic_gpio.h`, `esp_efuse.h`).

## Interface
- `[mpu.h:mpu_allocregion]`
- `[mpu.h:mpu_control]`
- `[mpu.h:mpu_modify_region]`
- `[mpu.h:mpu_configure_region]`
- `[mpu.h:mpu_initialize]`
- `[mpu.h:mpu_dump_region]`
- `[mpu.h:mpu_region_s]`
- `[mpu.h:MPU_VADDR_MASK]`
- `[mpu.h:MPU_ENTRY_AS]`
- `[mpu.h:MPU_ENTRY_AR]`
- `[mpu.h:MPU_AR_NONE]`
- `[mpu.h:MPU_AR_R]`
- `[mpu.h:MPU_AR_RX]`
- `[mpu.h:MPU_AR_RW]`
- `[mpu.h:MPU_AR_RWX]`
- `[mpu.h:MPU_AR_Ww]`
- `[mpu.h:MPU_AR_RWrwx]`
- `[mpu.h:MPU_AR_RWr]`
- `[mpu.h:MPU_AR_RWXrx]`
- `[xtensa.h:modifyreg8]`
- `[xtensa.h:modifyreg16]`
- `[xtensa.h:modifyreg32]`
- `[xtensa.h:xtensa_lowputs]`
- `[xtensa.h:xtensa_coproc_enable]`
- `[xtensa.h:xtensa_coproc_disable]`
- `[xtensa.h:xtensa_window_spill]`
- `[xtensa.h:xtensa_int_decode]`
- `[xtensa.h:xtensa_irq_dispatch]`
- `[xtensa.h:xtensa_enable_cpuint]`
- `[xtensa.h:xtensa_disable_cpuint]`
- [./espressif/README.md](./espressif/README.md)

## Invariants
- `[xtensa.h:#error]` Compile-time guard: CONFIG_IDLETHREAD_STACKSIZE is not defined
- `[xtensa_asm_utils.h:#error]` Compile-time guard: Unrecognized XCHAL_NUM_AREGS
- `[xtensa_timer.h:#error]` Compile-time guard: This Xtensa configuration is unsupported, it has no timers.
- `[xtensa_addrenv_kstack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[xtensa_cpenable.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[xtensa_cpuint.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[xtensa_createstack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[xtensa_debug.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[xtensa_exit.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[xtensa_fork.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[xtensa_irqdispatch.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[xtensa_irqdispatch.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation

## Side Effects
- `[xtensa.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[xtensa.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[xtensa.h:modifyreg32]` Performs atomic read-modify-write updates on 32-bit MMIO registers
- `[xtensa_counter.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[crt0.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)
- `[xtensa_backtrace.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)
- `[xtensa_cache.c:up_clean_dcache]` Flushes CPU data cache lines to main memory (`up_clean_dcache`)
- `[xtensa_cache.c:up_invalidate_dcache]` Invalidates CPU data cache lines prior to DMA/memory reads (`up_invalidate_dcache`)
- `[xtensa_cache.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)
- `[xtensa_cpuinfo.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)
- `[xtensa_cpuint.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)
- `[xtensa_debug.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)

## Verification
- Run: `make test`
