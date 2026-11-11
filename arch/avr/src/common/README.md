# common (`nuttx/arch/avr/src/common`)

## Overview
Hardware abstraction and architecture package for `common` under `nuttx/arch/avr/src/common`, providing 1 header file(s) and 11 source file(s) (including `avr_internal.h`, `avr_allocateheap.c`, `avr_exit.c`, `avr_getintstack.c`).

## Interface
- `[avr_internal.h:modifyreg8]`
- `[avr_internal.h:modifyreg16]`
- `[avr_internal.h:modifyreg32]`
- `[avr_internal.h:avr_dma_initialize]`
- `[avr_internal.h:avr_sigdeliver]`
- `[avr_internal.h:avr_lowputc]`
- `[avr_internal.h:avr_lowputs]`
- `[avr_internal.h:avr_addregion]`
- `[avr_internal.h:avr_lowinit]`
- `[avr_internal.h:avr_earlyserialinit]`
- `[avr_internal.h:avr_serialinit]`
- `[avr_internal.h:avr_netinitialize]`
- `[avr_internal.h:avr_usbinitialize]`
- `[avr_internal.h:avr_usbuninitialize]`
- `[avr_internal.h:avr_stack_check]`
- `[avr_internal.h:avr_color_intstack]`
- `[avr_internal.h:CONFIG_ARCH_INTERRUPTSTACK]`
- `[avr_internal.h:STACK_COLOR]`
- `[avr_internal.h:INTSTACK_COLOR]`
- `[avr_internal.h:HEAP_COLOR]`
- `[avr_internal.h:getreg8]`
- `[avr_internal.h:putreg8]`
- `[avr_internal.h:getreg16]`
- `[avr_internal.h:putreg16]`
- `[avr_internal.h:getreg32]`
- `[avr_internal.h:putreg32]`
- `[avr_allocateheap.c:up_allocate_heap]`
- `[avr_exit.c:up_exit]`
- `[avr_getintstack.c:up_get_intstackbase]`
- `[avr_idle.c:up_idle]`

## Invariants
- `[avr_modifyreg16.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[avr_modifyreg32.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[avr_modifyreg8.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)

## Side Effects
- `[avr_internal.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[avr_internal.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[avr_internal.h:modifyreg32]` Performs atomic read-modify-write updates on 32-bit MMIO registers
- `[avr_idle.c:nxsched_process_timer]` Advances the NuttX kernel system tick and scheduler timer state (`nxsched_process_timer`)
- `[avr_modifyreg16.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[avr_modifyreg32.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[avr_modifyreg32.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[avr_modifyreg32.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[avr_modifyreg8.c:putreg8]` Mutates 8-bit memory-mapped I/O (MMIO) hardware registers (`putreg8`)

## Verification
- Run: `make test`
