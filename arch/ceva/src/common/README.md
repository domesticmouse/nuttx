# common (`nuttx/arch/ceva/src/common`)

## Overview
Hardware abstraction and architecture package for `common` under `nuttx/arch/ceva/src/common`, providing 3 header file(s) and 29 source file(s) (including `ceva_internal.h`, `mpu.h`, `vintc.h`, `ceva_board.c`).

## Interface
- `[ceva_internal.h:modifyreg8]`
- `[ceva_internal.h:modifyreg16]`
- `[ceva_internal.h:modifyreg32]`
- `[ceva_internal.h:ceva_switchcontext]`
- `[ceva_internal.h:ceva_sigdeliver]`
- `[ceva_internal.h:ceva_earlyinitialize]`
- `[ceva_internal.h:ceva_lateinitialize]`
- `[ceva_internal.h:ceva_finalinitialize]`
- `[ceva_internal.h:ceva_pminitialize]`
- `[ceva_internal.h:ceva_reset]`
- `[ceva_internal.h:ceva_cpu_doze]`
- `[ceva_internal.h:ceva_cpu_idle]`
- `[ceva_internal.h:ceva_cpu_standby]`
- `[ceva_internal.h:ceva_cpu_sleep]`
- `[ceva_internal.h:ceva_cpu_normal]`
- `[ceva_internal.h:ceva_doirq]`
- `[ceva_internal.h:ceva_svcall]`
- `[ceva_internal.h:ceva_hardfault]`
- `[ceva_internal.h:ceva_svcall_handler]`
- `[ceva_internal.h:ceva_serialinit]`
- `[ceva_internal.h:ceva_earlyserialinit]`
- `[ceva_internal.h:ceva_dma_initialize]`
- `[ceva_internal.h:ceva_addregion]`
- `[ceva_internal.h:ceva_netinitialize]`
- `[ceva_internal.h:ceva_usbinitialize]`
- `[ceva_internal.h:ceva_usbuninitialize]`
- `[ceva_internal.h:ceva_stack_check]`
- `[ceva_internal.h:ceva_stack_color]`
- `[ceva_internal.h:ceva_color_intstack]`
- `[ceva_internal.h:USE_SERIALDRIVER]`

## Invariants
- `[ceva_board.c:#error]` Compile-time configuration constraint: CONFIG_BOARD_LATE_INITIALIZE is required for late initialization
- `[ceva_createstack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[ceva_exit.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[ceva_fork.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[ceva_heap.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[ceva_heap.c:#error]` Compile-time configuration constraint: CONFIG_ARCH_NR_MEMORY must between 1 to 4
- `[ceva_idle.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[ceva_modifyreg16.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[ceva_modifyreg32.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[ceva_modifyreg8.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[ceva_sigdeliver.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[ceva_start.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[ceva_internal.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[ceva_internal.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[ceva_internal.h:modifyreg32]` Performs atomic read-modify-write updates on 32-bit MMIO registers
- `[ceva_modifyreg16.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[ceva_modifyreg32.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[ceva_modifyreg32.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[ceva_modifyreg32.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[ceva_modifyreg8.c:putreg8]` Mutates 8-bit memory-mapped I/O (MMIO) hardware registers (`putreg8`)

## Verification
- Run: `make test`
