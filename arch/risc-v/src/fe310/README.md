# fe310 (`nuttx/arch/risc-v/src/fe310`)

## Overview
Hardware abstraction and architecture package for `fe310` (FE310 Configuration Options; FE310 Peripheral Support) under `nuttx/arch/risc-v/src/fe310`, providing 7 header file(s) and 10 source file(s) (including `chip.h`, `fe310.h`, `fe310_clockconfig.h`, `fe310_config.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/risc-v/src/fe310/hardware`, providing 6 header file(s) and 0 source file(s) (including `fe310_clint.h`, `fe310_gpio.h`, `fe310_memorymap.h`, `fe310_plic.h`).

## Interface
- `[fe310_clockconfig.h:fe310_get_hfclk]`
- `[fe310_clockconfig.h:fe310_clockconfig]`
- `[fe310_config.h:HAVE_UART_DEVICE]`
- `[fe310_config.h:HAVE_SERIAL_CONSOLE]`
- `[fe310_gpio.h:fe310_gpio_config]`
- `[fe310_gpio.h:fe310_gpio_write]`
- `[fe310_gpio.h:fe310_gpio_read]`
- `[fe310_gpio.h:fe310_gpio_clearpending]`
- `[fe310_gpio.h:GPIO_MODE_SHIFT]`
- `[fe310_gpio.h:GPIO_MODE_MASK]`
- `[fe310_gpio.h:GPIO_MODE_INPUT]`
- `[fe310_gpio.h:GPIO_MODE_OUTPUT]`
- `[fe310_gpio.h:GPIO_MODE_INIRQ]`
- `[fe310_gpio.h:GPIO_MODE_OUTPUT_INV]`
- `[fe310_gpio.h:GPIO_VALUE_SHIFT]`
- `[fe310_gpio.h:GPIO_VALUE_MASK]`
- `[fe310_gpio.h:GPIO_VALUE_ZERO]`
- `[fe310_gpio.h:GPIO_VALUE_ONE]`
- `[fe310_gpio.h:GPIO_IOF_SHIFT]`
- `[fe310_gpio.h:GPIO_IOF_MASK]`
- `[fe310_lowputc.h:fe310_lowsetup]`
- `[fe310_memorymap.h:FE310_IDLESTACK_BASE]`
- `[fe310_memorymap.h:FE310_IDLESTACK_TOP]`
- `[fe310_allocateheap.c:riscv_addregion]`
- `[fe310_clockconfig.c:fe310_get_hfclk]`
- `[fe310_clockconfig.c:fe310_clockconfig]`
- `[fe310_gpio.c:fe310_gpio_config]`
- `[fe310_gpio.c:fe310_gpio_write]`
- `[fe310_gpio.c:fe310_gpio_read]`
- `[fe310_gpio.c:fe310_gpio_clearpending]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[fe310_clockconfig.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[fe310_gpio.c:ASSERT]` Enforces unconditional runtime assertions via `ASSERT`
- `[fe310_gpio.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[fe310_irq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[fe310_irq.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[fe310_serial.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[fe310_serial.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[fe310_serial.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[fe310_serial.c:#error]` Compile-time configuration constraint: I'm confused... Do we have a serial console or not?
- `[fe310_timerisr.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[fe310_clockconfig.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[fe310_clockconfig.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[fe310_clockconfig.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[fe310_gpio.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[fe310_gpio.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[fe310_idle.c:nxsched_process_timer]` Advances the NuttX kernel system tick and scheduler timer state (`nxsched_process_timer`)
- `[fe310_irq.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[fe310_irq.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[fe310_irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[fe310_irq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[fe310_irq_dispatch.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[fe310_irq_dispatch.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)

## Verification
- Run: `make test`
