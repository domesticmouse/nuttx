# a1x (`nuttx/arch/arm/src/a1x`)

## Overview
Hardware abstraction and architecture package for `a1x` (A1x Configuration Options; Allwinner A1X Peripheral Support) under `nuttx/arch/arm/src/a1x`, providing 7 header file(s) and 6 source file(s) (including `a1x_boot.h`, `a1x_config.h`, `a1x_irq.h`, `a1x_lowputc.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/a1x/hardware`, providing 8 header file(s) and 0 source file(s) (including `a10_memorymap.h`, `a10_piocfg.h`, `a1x_intc.h`, `a1x_memorymap.h`).

## Interface
- `[a1x_boot.h:a1x_boardinitialize]`
- `[a1x_config.h:HAVE_UART_DEVICE]`
- `[a1x_config.h:HAVE_SERIAL_CONSOLE]`
- `[a1x_irq.h:SCRTYPE_NTYPES]`
- `[a1x_irq.h:A1X_DEFAULT_PRIOR]`
- `[a1x_lowputc.h:a1x_lowsetup]`
- `[a1x_pio.h:a1x_pio_irqinitialize]`
- `[a1x_pio.h:a1x_pio_config]`
- `[a1x_pio.h:a1x_pio_write]`
- `[a1x_pio.h:a1x_pio_read]`
- `[a1x_pio.h:a1x_pio_irqenable]`
- `[a1x_pio.h:a1x_pio_irqdisable]`
- `[a1x_pio.h:pio_pinset_t]`
- `[a1x_pio.h:PIO_MODE_SHIFT]`
- `[a1x_pio.h:PIO_MODE_MASK]`
- `[a1x_pio.h:PIO_PERIPH0]`
- `[a1x_pio.h:PIO_PERIPH1]`
- `[a1x_pio.h:PIO_PERIPH2]`
- `[a1x_pio.h:PIO_PERIPH3]`
- `[a1x_pio.h:PIO_PERIPH4]`
- `[a1x_pio.h:PIO_PERIPH5]`
- `[a1x_pio.h:PIO_PERIPH6]`
- `[a1x_pio.h:PIO_PERIPH7]`
- `[a1x_pio.h:PIO_INPUT]`
- `[a1x_pio.h:PIO_OUTPUT]`
- `[a1x_serial.h:UART_MINDL]`
- `[a1x_boot.c:arm_boot]`
- `[a1x_irq.c:up_irqinitialize]`
- `[a1x_irq.c:arm_decodeirq]`
- `[a1x_irq.c:up_disable_irq]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[a1x_boot.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[a1x_boot.c:#error]` Compile-time configuration constraint: High vector remap cannot be performed if we are using a ROM page table
- `[a1x_irq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[a1x_irq.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[a1x_lowputc.c:#error]` Compile-time configuration constraint: No CONFIG_UARTn_SERIAL_CONSOLE Setting
- `[a1x_pio.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[a1x_serial.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[a1x_serial.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[a1x_timerisr.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[a1x_irq.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[a1x_irq.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[a1x_irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[a1x_irq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[a1x_lowputc.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[a1x_lowputc.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[a1x_pio.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[a1x_pio.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[a1x_pio.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[a1x_pio.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[a1x_serial.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[a1x_serial.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)

## Verification
- Run: `make test`
