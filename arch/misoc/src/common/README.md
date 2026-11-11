# common (`nuttx/arch/misoc/src/common`)

## Overview
Hardware abstraction and architecture package for `common` under `nuttx/arch/misoc/src/common`, providing 1 header file(s) and 10 source file(s) (including `misoc.h`, `misoc_flushcache.c`, `misoc_initialize.c`, `misoc_lowputs.c`).

## Subdirectories & Boundaries
- `hw`: [./hw/README.md](./hw/README.md) - Hardware abstraction and architecture package for `hw` under `nuttx/arch/misoc/src/common/hw`, providing 3 header file(s) and 0 source file(s) (including `common.h`, `ethmac_mem.h`, `flags.h`).

## Interface
- `[misoc.h:flush_cpu_dcache]`
- `[misoc.h:misoc_serial_initialize]`
- `[misoc.h:misoc_net_initialize]`
- `[misoc.h:misoc_puts]`
- `[misoc.h:misoc_lowputc]`
- `[misoc.h:misoc_lowputs]`
- `[misoc.h:modifyreg8]`
- `[misoc.h:modifyreg16]`
- `[misoc.h:modifyreg32]`
- `[misoc.h:misoc_flush_dcache]`
- `[misoc.h:misoc_flush_icache]`
- `[misoc.h:getreg8]`
- `[misoc.h:putreg8]`
- `[misoc.h:getreg16]`
- `[misoc.h:putreg16]`
- `[misoc.h:getreg32]`
- `[misoc.h:putreg32]`
- `[misoc_flushcache.c:misoc_flush_dcache]`
- `[misoc_flushcache.c:misoc_flush_icache]`
- `[misoc_initialize.c:up_initialize]`
- `[misoc_lowputs.c:misoc_lowputs]`
- `[misoc_modifyreg16.c:modifyreg16]`
- `[misoc_modifyreg32.c:modifyreg32]`
- `[misoc_modifyreg8.c:modifyreg8]`
- `[misoc_net.c:misoc_net_initialize]`
- `[misoc_puts.c:misoc_puts]`
- `[misoc_serial.c:misoc_earlyserialinit]`
- `[misoc_serial.c:up_putc]`
- `[misoc_serial.c:misoc_serial_initialize]`
- `[misoc_serial.c:misoc_lowputc]`
- [./hw/README.md](./hw/README.md)

## Invariants
- `[misoc_modifyreg16.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[misoc_modifyreg32.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[misoc_modifyreg8.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[misoc_net.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[misoc_net.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[misoc_net.c:#error]` Compile-time configuration constraint: High priority work queue support is required
- `[misoc_serial.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[misoc_serial.c:#error]` Compile-time configuration constraint: I'm confused... Do we have a serial console or not?
- `[misoc_timerisr.c:#error]` Compile-time configuration constraint: SYSTICK_RELOAD exceeds the range of the RELOAD register

## Side Effects
- `[misoc.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[misoc.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[misoc.h:modifyreg32]` Performs atomic read-modify-write updates on 32-bit MMIO registers
- `[misoc_modifyreg16.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[misoc_modifyreg32.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[misoc_modifyreg32.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[misoc_modifyreg32.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[misoc_modifyreg8.c:putreg8]` Mutates 8-bit memory-mapped I/O (MMIO) hardware registers (`putreg8`)
- `[misoc_net.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[misoc_net.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[misoc_net.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[misoc_serial.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)

## Verification
- Run: `make test`
