# armv7-r (`nuttx/arch/arm/src/armv7-r`)

## Overview
Hardware abstraction and architecture package for `armv7-r` (ARMv7-R Configuration Options; L2 Cache Configuration) under `nuttx/arch/arm/src/armv7-r`, providing 11 header file(s) and 21 source file(s) (including `arm.h`, `arm_timer.h`, `cp15_cacheops.h`, `gic.h`).

## Interface
- `[arm.h:arm_boot]`
- `[arm.h:arm_data_initialize]`
- `[arm.h:PSR_MODE_SHIFT]`
- `[arm.h:PSR_MODE_MASK]`
- `[arm.h:PSR_MODE_USR]`
- `[arm.h:PSR_MODE_FIQ]`
- `[arm.h:PSR_MODE_IRQ]`
- `[arm.h:PSR_MODE_SVC]`
- `[arm.h:PSR_MODE_ABT]`
- `[arm.h:PSR_MODE_UND]`
- `[arm.h:PSR_MODE_SYS]`
- `[arm.h:PSR_T_BIT]`
- `[arm.h:PSR_MASK_SHIFT]`
- `[arm.h:PSR_MASK_MASK]`
- `[arm_timer.h:arm_timer_initialize]`
- `[arm_timer.h:arm_timer_get_freq]`
- `[cp15_cacheops.h:cp15_invalidate_icache]`
- `[cp15_cacheops.h:cp15_dcache_op_level]`
- `[cp15_cacheops.h:cp15_coherent_dcache]`
- `[cp15_cacheops.h:cp15_invalidate_dcache]`
- `[cp15_cacheops.h:cp15_invalidate_dcache_all]`
- `[cp15_cacheops.h:cp15_clean_dcache]`
- `[cp15_cacheops.h:cp15_clean_dcache_all]`
- `[cp15_cacheops.h:cp15_flush_dcache]`
- `[cp15_cacheops.h:cp15_flush_dcache_all]`
- `[cp15_cacheops.h:cp15_icache_size]`
- `[cp15_cacheops.h:cp15_dcache_size]`
- `[cp15_cacheops.h:cp15_icache_linesize]`
- `[cp15_cacheops.h:cp15_dcache_linesize]`
- `[cp15_cacheops.h:CP15_CACHE_INVALIDATE]`

## Invariants
- `[mpu.h:#error]` Compile-time guard: FIXME: Unsupported number of MPU regions
- `[smp.h:#error]` Compile-time guard: This logic needs to extended for CONFIG_SMP_NCPUS > 4
- `[arm_cpuidlestack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[arm_cpustart.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[arm_doirq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[arm_doirq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[arm_gicv2.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[arm_l2cc_pl310.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[arm_l2cc_pl310.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[arm_l2cc_pl310.c:#error]` Compile-time configuration constraint: Number of ways not selected
- `[arm_mpu.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[gic.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[gic.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[arm_cache.c:up_clean_dcache]` Flushes CPU data cache lines to main memory (`up_clean_dcache`)
- `[arm_cache.c:up_invalidate_dcache]` Invalidates CPU data cache lines prior to DMA/memory reads (`up_invalidate_dcache`)
- `[arm_gicv2.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[arm_gicv2.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[arm_gicv2.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[arm_gicv2.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[arm_gicv2.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[arm_gicv2_dump.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[arm_l2cc_pl310.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[arm_l2cc_pl310.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)

## Verification
- Run: `make test`
