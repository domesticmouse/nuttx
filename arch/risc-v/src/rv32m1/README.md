# rv32m1 (`nuttx/arch/risc-v/src/rv32m1`)

## Overview
Hardware abstraction and architecture package for `rv32m1` (RV32M1 Configuration Options; RV32M1 Peripheral Support) under `nuttx/arch/risc-v/src/rv32m1`, providing 10 header file(s) and 12 source file(s) (including `chip.h`, `rv32m1.h`, `rv32m1_clockconfig.h`, `rv32m1_gpio.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/risc-v/src/rv32m1/hardware`, providing 16 header file(s) and 0 source file(s) (including `rv32m1_eu.h`, `rv32m1_gpio.h`, `rv32m1_intmux.h`, `rv32m1_lpit.h`).

## Interface
- `[rv32m1_clockconfig.h:rv32m1_clockconfig]`
- `[rv32m1_clockconfig.h:rv32m1_clockfreq]`
- `[rv32m1_clockconfig.h:clk_e]`
- `[rv32m1_gpio.h:rv32m1_gpio_config]`
- `[rv32m1_gpio.h:rv32m1_gpio_write]`
- `[rv32m1_gpio.h:rv32m1_gpio_toggle]`
- `[rv32m1_gpio.h:rv32m1_gpio_read]`
- `[rv32m1_gpio.h:rv32m1_gpio_irqenable]`
- `[rv32m1_gpio.h:rv32m1_gpio_irqdisable]`
- `[rv32m1_gpio.h:rv32m1_gpio_irqattach]`
- `[rv32m1_gpio.h:rv32m1_gpio_irqdetach]`
- `[rv32m1_gpio.h:rv32m1_gpio_clearpending]`
- `[rv32m1_gpio.h:GPIO_MODE_SHIFT]`
- `[rv32m1_gpio.h:GPIO_MODE_MASK]`
- `[rv32m1_gpio.h:GPIO_INPUT]`
- `[rv32m1_gpio.h:GPIO_OUTPUT]`
- `[rv32m1_gpio.h:GPIO_ALT]`
- `[rv32m1_gpio.h:GPIO_PUPD_SHIFT]`
- `[rv32m1_gpio.h:GPIO_PUPD_MASK]`
- `[rv32m1_gpio.h:GPIO_FLOAT]`
- `[rv32m1_gpio.h:GPIO_PULLUP]`
- `[rv32m1_gpio.h:GPIO_PULLDOWN]`
- `[rv32m1_gpio.h:GPIO_AF_SHIFT]`
- `[rv32m1_gpio.h:GPIO_AF_MASK]`
- `[rv32m1_linker.h:SECTION_ITCM]`
- `[rv32m1_linker.h:SECTION_UITCM]`
- `[rv32m1_linker.h:LOCATE_ITCM]`
- `[rv32m1_linker.h:LOCATE_UITCM]`
- `[rv32m1_lowputc.h:rv32m1_lowsetup]`
- `[rv32m1_memorymap.h:RV32M1_IDLESTACK_BASE]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[rv32m1_delay.c:static_assert]` Enforces compile-time size and alignment invariants via `static_assert`
- `[rv32m1_gpio.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[rv32m1_irq.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[rv32m1_serial.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[rv32m1_serial.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[rv32m1_serial.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[rv32m1_serial.c:#error]` Compile-time configuration constraint: No Serial Consoles for RV32M1

## Side Effects
- `[rv32m1_clockconfig.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[rv32m1_clockconfig.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[rv32m1_gpio.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[rv32m1_gpio.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[rv32m1_gpio.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[rv32m1_gpio.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[rv32m1_irq.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[rv32m1_irq.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[rv32m1_irq.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[rv32m1_irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[rv32m1_irq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[rv32m1_irq_dispatch.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)

## Verification
- Run: `make test`
