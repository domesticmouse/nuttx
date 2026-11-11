# k210 (`nuttx/arch/risc-v/src/k210`)

## Overview
Hardware abstraction and architecture package for `k210` (K210 Configuration Options; K210 Peripheral Support) under `nuttx/arch/risc-v/src/k210`, providing 11 header file(s) and 13 source file(s) (including `chip.h`, `k210.h`, `k210_clockconfig.h`, `k210_config.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/risc-v/src/k210/hardware`, providing 6 header file(s) and 0 source file(s) (including `k210_clint.h`, `k210_memorymap.h`, `k210_plic.h`, `k210_sysctl.h`).

## Interface
- `[k210_clockconfig.h:k210_get_cpuclk]`
- `[k210_clockconfig.h:k210_get_pll0clk]`
- `[k210_clockconfig.h:k210_clockconfig]`
- `[k210_config.h:HAVE_UART_DEVICE]`
- `[k210_config.h:HAVE_SERIAL_CONSOLE]`
- `[k210_fpioa.h:k210_fpioa_config]`
- `[k210_fpioa.h:K210_IO_NUMBER]`
- `[k210_fpioa.h:K210_IO_FUNC_UARTHS_RX]`
- `[k210_fpioa.h:K210_IO_FUNC_UARTHS_TX]`
- `[k210_fpioa.h:K210_IO_FUNC_GPIOHS0]`
- `[k210_fpioa.h:K210_IO_FUNC_GPIOHS1]`
- `[k210_fpioa.h:K210_IO_FUNC_GPIOHS2]`
- `[k210_fpioa.h:K210_IO_FUNC_GPIOHS3]`
- `[k210_fpioa.h:K210_IO_FUNC_GPIOHS4]`
- `[k210_fpioa.h:K210_IO_FUNC_GPIOHS5]`
- `[k210_fpioa.h:K210_IO_FUNC_GPIOHS6]`
- `[k210_fpioa.h:K210_IO_FUNC_GPIOHS7]`
- `[k210_fpioa.h:K210_IO_FUNC_GPIOHS8]`
- `[k210_gpiohs.h:k210_gpiohs_set_direction]`
- `[k210_gpiohs.h:k210_gpiohs_set_value]`
- `[k210_gpiohs.h:k210_gpiohs_get_value]`
- `[k210_lowputc.h:k210_lowsetup]`
- `[k210_memorymap.h:K210_IDLESTACK_BASE]`
- `[k210_memorymap.h:K210_IDLESTACK0_BASE]`
- `[k210_sysctl.h:k210_sysctl_init]`
- `[k210_sysctl.h:k210_sysctl_clock_enable]`
- `[k210_sysctl.h:k210_sysctl_clock_disable]`
- `[k210_sysctl.h:k210_sysctl_clock_get_freq]`
- `[k210_sysctl.h:k210_sysctl_cpu_get_freq]`
- `[k210_sysctl.h:k210_sysctl_cpu_set_freq]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[k210_allocateheap.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[k210_fpioa.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[k210_irq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[k210_irq.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[k210_serial.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[k210_serial.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[k210_serial.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[k210_serial.c:#error]` Compile-time configuration constraint: I'm confused... Do we have a serial console or not?
- `[k210_timerisr.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[k210_userspace.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[k210_wdt.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates

## Side Effects
- `[k210_clockconfig.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[k210_fpioa.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[k210_gpiohs.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[k210_gpiohs.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[k210_irq.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[k210_irq.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[k210_irq.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[k210_irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[k210_irq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[k210_irq_dispatch.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[k210_irq_dispatch.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[k210_lowputc.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)

## Verification
- Run: `make test`
