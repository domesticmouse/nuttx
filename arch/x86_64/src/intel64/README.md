# intel64 (`nuttx/arch/x86_64/src/intel64`)

## Overview
Hardware abstraction and architecture package for `intel64` (intel64 Configuration Options) under `nuttx/arch/x86_64/src/intel64`, providing 6 header file(s) and 41 source file(s) (including `chip.h`, `intel64.h`, `intel64_cpu.h`, `intel64_hpet.h`).

## Interface
- `[intel64.h:vector_isr0]`
- `[intel64.h:vector_isr1]`
- `[intel64.h:vector_isr2]`
- `[intel64.h:vector_isr3]`
- `[intel64.h:vector_isr4]`
- `[intel64.h:vector_isr5]`
- `[intel64.h:vector_isr6]`
- `[intel64.h:vector_isr7]`
- `[intel64.h:vector_isr8]`
- `[intel64.h:vector_isr9]`
- `[intel64.h:vector_isr10]`
- `[intel64.h:vector_isr11]`
- `[intel64.h:vector_isr12]`
- `[intel64.h:vector_isr13]`
- `[intel64.h:vector_isr14]`
- `[intel64.h:vector_isr15]`
- `[intel64.h:vector_isr16]`
- `[intel64.h:vector_isr17]`
- `[intel64.h:vector_isr18]`
- `[intel64.h:vector_isr19]`
- `[intel64.h:vector_isr20]`
- `[intel64.h:vector_isr21]`
- `[intel64.h:vector_isr22]`
- `[intel64.h:vector_isr23]`
- `[intel64.h:vector_isr24]`
- `[intel64.h:vector_isr25]`
- `[intel64.h:vector_isr26]`
- `[intel64.h:vector_isr27]`
- `[intel64.h:vector_isr28]`
- `[intel64.h:vector_isr29]`

## Invariants
- `[intel64_cpu.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[intel64_cpu.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[intel64_cpuidlestack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[intel64_createstack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[intel64_freq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[intel64_handlers.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[intel64_handlers.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[intel64_hpet.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[intel64_hpet.c:ASSERT]` Enforces unconditional runtime assertions via `ASSERT`
- `[intel64_initialstate.c:#error]` Compile-time configuration constraint: XCPTCONTEXT_SIZE must be aligned to XCPTCONTEXT_ALIGN !
- `[intel64_irq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[intel64_irq.c:ASSERT]` Enforces unconditional runtime assertions via `ASSERT`

## Side Effects
- `[intel64_cache.c:up_clean_dcache]` Flushes CPU data cache lines to main memory (`up_clean_dcache`)
- `[intel64_cache.c:up_invalidate_dcache]` Invalidates CPU data cache lines prior to DMA/memory reads (`up_invalidate_dcache`)
- `[intel64_cache.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)
- `[intel64_check_capability.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)
- `[intel64_cpu.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)
- `[intel64_hpet.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[intel64_hpet.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[intel64_hpet.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[intel64_idle.c:nxsched_process_timer]` Advances the NuttX kernel system tick and scheduler timer state (`nxsched_process_timer`)
- `[intel64_idle.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)
- `[intel64_initialstate.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)
- `[intel64_irq.c:outb]` Writes bytes to CPU I/O ports (`outb`)

## Verification
- Run: `make test`
