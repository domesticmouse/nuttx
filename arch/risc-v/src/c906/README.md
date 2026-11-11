# c906 (`nuttx/arch/risc-v/src/c906`)

## Overview
Hardware abstraction and architecture package for `c906` (C906 Configuration Options; C906 Peripheral Support) under `nuttx/arch/risc-v/src/c906`, providing 7 header file(s) and 9 source file(s) (including `c906.h`, `c906_clockconfig.h`, `c906_config.h`, `c906_lowputc.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/risc-v/src/c906/hardware`, providing 5 header file(s) and 0 source file(s) (including `c906_clint.h`, `c906_memorymap.h`, `c906_plic.h`, `c906_sysctl.h`).

## Interface
- `[c906_clockconfig.h:c906_get_cpuclk]`
- `[c906_clockconfig.h:c906_get_pll0clk]`
- `[c906_clockconfig.h:c906_clockconfig]`
- `[c906_config.h:HAVE_UART_DEVICE]`
- `[c906_config.h:HAVE_SERIAL_CONSOLE]`
- `[c906_lowputc.h:c906_lowsetup]`
- `[c906_memorymap.h:C906_IDLESTACK_BASE]`
- `[c906_memorymap.h:C906_IDLESTACK0_TOP]`
- `[c906_memorymap.h:C906_IDLESTACK_TOP]`
- `[c906_userspace.h:c906_userspace]`
- `[c906_allocateheap.c:up_allocate_heap]`
- `[c906_allocateheap.c:up_allocate_kheap]`
- `[c906_allocateheap.c:riscv_addregion]`
- `[c906_clockconfig.c:c906_get_cpuclk]`
- `[c906_clockconfig.c:c906_get_pll0clk]`
- `[c906_clockconfig.c:c906_clockconfig]`
- `[c906_irq.c:up_irqinitialize]`
- `[c906_irq.c:up_disable_irq]`
- `[c906_irq.c:up_enable_irq]`
- `[c906_irq.c:riscv_ack_irq]`
- `[c906_irq.c:up_irq_enable]`
- `[c906_irq_dispatch.c:riscv_dispatch_irq]`
- `[c906_lowputc.c:riscv_lowputc]`
- `[c906_lowputc.c:c906_lowsetup]`
- `[c906_serial.c:riscv_earlyserialinit]`
- `[c906_serial.c:riscv_serialinit]`
- `[c906_serial.c:up_putc]`
- `[c906_start.c:__c906_start]`
- `[c906_start.c:showprogress]`
- `[c906_timerisr.c:up_timer_initialize]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[c906_irq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[c906_irq.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[c906_serial.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[c906_serial.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[c906_serial.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[c906_serial.c:#error]` Compile-time configuration constraint: I'm confused... Do we have a serial console or not?
- `[c906_timerisr.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[c906_userspace.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[c906_irq.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[c906_irq.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[c906_irq.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[c906_irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[c906_irq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[c906_irq_dispatch.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[c906_irq_dispatch.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[c906_lowputc.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[c906_lowputc.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[c906_serial.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[c906_serial.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[c906_serial.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)

## Verification
- Run: `make test`
