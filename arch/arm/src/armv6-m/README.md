# armv6-m (`nuttx/arch/arm/src/armv6-m`)

## Overview
Hardware abstraction and architecture package for `armv6-m` (ARMv6-M Configuration Options) under `nuttx/arch/arm/src/armv6-m`, providing 4 header file(s) and 14 source file(s) (including `exc_return.h`, `nvic.h`, `psr.h`, `ram_vectors.h`).

## Interface
- `[exc_return.h:EXC_RETURN_BASE]`
- `[exc_return.h:EXC_RETURN_PROCESS_BITNO]`
- `[exc_return.h:EXC_RETURN_PROCESS_STACK]`
- `[exc_return.h:EXC_RETURN_THREAD_BITNO]`
- `[exc_return.h:EXC_RETURN_THREAD_MODE]`
- `[exc_return.h:EXC_RETURN_HANDLER]`
- `[exc_return.h:EXC_RETURN_THREAD]`
- `[nvic.h:arm_dumpnvic]`
- `[nvic.h:NVIC_IRQ_NMI]`
- `[nvic.h:NVIC_IRQ_HARDFAULT]`
- `[nvic.h:NVIC_IRQ_MEMFAULT]`
- `[nvic.h:NVIC_IRQ_BUSFAULT]`
- `[nvic.h:NVIC_IRQ_USAGEFAULT]`
- `[nvic.h:NVIC_IRQ_SVCALL]`
- `[nvic.h:NVIC_IRQ_DBGMONITOR]`
- `[nvic.h:NVIC_IRQ_PENDSV]`
- `[nvic.h:NVIC_IRQ_SYSTICK]`
- `[nvic.h:NVIC_IRQ_FIRST]`
- `[nvic.h:ARMV6M_SYSCON1_BASE]`
- `[nvic.h:ARMV6M_SYSTICK_BASE]`
- `[psr.h:ARMV6M_APSR_V]`
- `[psr.h:ARMV6M_APSR_C]`
- `[psr.h:ARMV6M_APSR_Z]`
- `[psr.h:ARMV6M_APSR_N]`
- `[psr.h:ARMV6M_IPSR_ISR_SHIFT]`
- `[psr.h:ARMV6M_IPSR_ISR_MASK]`
- `[psr.h:ARMV6M_EPSR_T]`
- `[psr.h:ARMV6M_XPSR_ISR_SHIFT]`
- `[psr.h:ARMV6M_XPSR_ISR_MASK]`
- `[psr.h:ARMV6M_XPSR_T]`

## Invariants
- `[arm_doirq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[arm_doirq.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[arm_dumpnvic.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[arm_hardfault.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[arm_hardfault.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[arm_ramvec_attach.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[arm_ramvec_initialize.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[arm_sigdeliver.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[arm_sigdeliver.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[arm_sigdeliver.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[arm_svcall.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[arm_trigger_irq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[arm_cpuinfo.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[arm_dumpnvic.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[arm_initialstate.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)
- `[arm_ramvec_attach.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[arm_ramvec_initialize.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[arm_ramvec_initialize.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[arm_systemreset.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[arm_trigger_irq.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[arm_trigger_irq.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)

## Verification
- Run: `make test`
