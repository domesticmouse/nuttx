# common (`nuttx/arch/tricore/src/common`)

## Overview
Hardware abstraction and architecture package for `common` under `nuttx/arch/tricore/src/common`, providing 2 header file(s) and 32 source file(s) (including `tricore_internal.h`, `tricore_mpu.h`, `tricore_allocateheap.c`, `tricore_backtrace.c`).

## Interface
- `[tricore_internal.h:tricore_ack_irq]`
- `[tricore_internal.h:tricore_doirq]`
- `[tricore_internal.h:tricore_sigdeliver]`
- `[tricore_internal.h:tricore_svcall]`
- `[tricore_internal.h:tricore_trapcall]`
- `[tricore_internal.h:tricore_trapinit]`
- `[tricore_internal.h:tricore_bustrap_register_hook]`
- `[tricore_internal.h:tricore_fcu_register_pool]`
- `[tricore_internal.h:tricore_fcu_recover]`
- `[tricore_internal.h:tricore_alloc_csa]`
- `[tricore_internal.h:tricore_reclaim_csa]`
- `[tricore_internal.h:tricore_lowputc]`
- `[tricore_internal.h:tricore_lowputs]`
- `[tricore_internal.h:tricore_serialinit]`
- `[tricore_internal.h:tricore_earlyserialinit]`
- `[tricore_internal.h:tricore_fpuinit]`
- `[tricore_internal.h:tricore_init_dbgmonitor]`
- `[tricore_internal.h:tricore_systimer_initialize]`
- `[tricore_internal.h:tricore_stack_check]`
- `[tricore_internal.h:tricore_stack_color]`
- `[tricore_internal.h:tricore_trap_s]`
- `[tricore_internal.h:SCU_FREQUENCY]`
- `[tricore_internal.h:USE_SERIALDRIVER]`
- `[tricore_internal.h:USE_EARLYSERIALINIT]`
- `[tricore_internal.h:CONFIG_ARCH_INTERRUPTSTACK]`
- `[tricore_internal.h:INTSTACK_SIZE]`
- `[tricore_internal.h:STACK_COLOR]`
- `[tricore_internal.h:INTSTACK_COLOR]`
- `[tricore_internal.h:HEAP_COLOR]`
- `[tricore_internal.h:getreg8]`

## Invariants
- `[tricore_createstack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[tricore_doirq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[tricore_doirq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[tricore_exit.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[tricore_irq.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[tricore_mpu.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[tricore_sigdeliver.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[tricore_sigdeliver.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[tricore_systimer.c:ASSERT]` Enforces unconditional runtime assertions via `ASSERT`
- `[tricore_systimer.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[tricore_systimer.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[tricore_trapcall.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[tricore_internal.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[tricore_internal.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[tricore_cache.c:up_clean_dcache]` Flushes CPU data cache lines to main memory (`up_clean_dcache`)
- `[tricore_cache.c:up_invalidate_dcache]` Invalidates CPU data cache lines prior to DMA/memory reads (`up_invalidate_dcache`)
- `[tricore_cache.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)
- `[tricore_hwdebug.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[tricore_hwdebug.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)
- `[tricore_idle.c:nxsched_process_timer]` Advances the NuttX kernel system tick and scheduler timer state (`nxsched_process_timer`)
- `[tricore_idle.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)
- `[tricore_irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[tricore_irq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[tricore_irq.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)

## Verification
- Run: `make test`
