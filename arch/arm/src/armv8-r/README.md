# armv8-r (`nuttx/arch/arm/src/armv8-r`)

## Overview
Hardware abstraction and architecture package for `armv8-r` (ARMv8-R Configuration Options; L2 Cache Configuration) under `nuttx/arch/arm/src/armv8-r`, providing 7 header file(s) and 16 source file(s) (including `arm.h`, `arm_gic.h`, `arm_timer.h`, `cp15_cacheops.h`).

## Interface
- `[arm.h:arm_boot]`
- `[arm.h:arm_data_initialize]`
- `[arm.h:BIT]`
- `[arm.h:BIT64]`
- `[arm.h:BIT_MASK]`
- `[arm.h:BIT64_MASK]`
- `[arm.h:PSR_MODE_SHIFT]`
- `[arm.h:PSR_MODE_MASK]`
- `[arm.h:PSR_MODE_USR]`
- `[arm.h:PSR_MODE_FIQ]`
- `[arm.h:PSR_MODE_IRQ]`
- `[arm.h:PSR_MODE_SVC]`
- `[arm.h:PSR_MODE_ABT]`
- `[arm.h:PSR_MODE_HYP]`
- `[arm_gic.h:arm_gic_irq_is_enabled]`
- `[arm_gic.h:arm_gic_initialize]`
- `[arm_gic.h:arm_gic_irq_set_priority]`
- `[arm_gic.h:arm_gic_set_group]`
- `[arm_gic.h:arm_gic_raise_sgi]`
- `[arm_gic.h:arm_smp_sched_handler]`
- `[arm_gic.h:arm_gic_secondary_init]`
- `[arm_gic.h:GIC_DIST_BASE]`
- `[arm_gic.h:GICD_CTLR]`
- `[arm_gic.h:GICD_TYPER]`
- `[arm_gic.h:GICD_IIDR]`
- `[arm_gic.h:GICD_STATUSR]`
- `[arm_gic.h:GICD_SETSPI_NSR]`
- `[arm_gic.h:GICD_CLRSPI_NSR]`
- `[arm_gic.h:GICD_SETSPI_SR]`
- `[arm_gic.h:GICD_CLRSPI_SR]`

## Invariants
- `[arm_dofiq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[arm_doirq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[arm_doirq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[arm_gicv3.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[arm_gicv3.c:ASSERT]` Enforces unconditional runtime assertions via `ASSERT`
- `[arm_gicv3.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[arm_gicv3.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[arm_l2cc_pl310.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[arm_l2cc_pl310.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[arm_l2cc_pl310.c:#error]` Compile-time configuration constraint: Number of ways not selected

## Side Effects
- `[arm_cache.c:up_clean_dcache]` Flushes CPU data cache lines to main memory (`up_clean_dcache`)
- `[arm_cache.c:up_invalidate_dcache]` Invalidates CPU data cache lines prior to DMA/memory reads (`up_invalidate_dcache`)
- `[arm_gicv3.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[arm_gicv3.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[arm_gicv3.c:putreg8]` Mutates 8-bit memory-mapped I/O (MMIO) hardware registers (`putreg8`)
- `[arm_gicv3.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[arm_gicv3.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[arm_gicv3.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[arm_l2cc_pl310.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[arm_l2cc_pl310.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[arm_syscall.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)
- `[arm_timer.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)

## Verification
- Run: `make test`
