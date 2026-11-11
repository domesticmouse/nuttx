# hpm6000 (`nuttx/arch/risc-v/src/hpm6000`)

## Overview
Hardware abstraction and architecture package for `hpm6000` (HPM6000 Configuration Options; HPM6000 Peripheral Selection) under `nuttx/arch/risc-v/src/hpm6000`, providing 11 header file(s) and 9 source file(s) (including `chip.h`, `hpm.h`, `hpm_clockconfig.h`, `hpm_config.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/risc-v/src/hpm6000/hardware`, providing 8 header file(s) and 0 source file(s) (including `hpm_gpio.h`, `hpm_ioc.h`, `hpm_mchtmr.h`, `hpm_memorymap.h`).

## Interface
- `[hpm_clockconfig.h:hpm_get_osc_freq]`
- `[hpm_clockconfig.h:hpm_clockconfig]`
- `[hpm_clockconfig.h:hpm_uart_clockconfig]`
- `[hpm_clockconfig.h:clock_node_t]`
- `[hpm_clockconfig.h:clock_source_t]`
- `[hpm_clockconfig.h:CPU_DIV]`
- `[hpm_clockconfig.h:AXI_SUB_DIV]`
- `[hpm_clockconfig.h:AHB_SUB_DIV]`
- `[hpm_clockconfig.h:PLL1_DIV]`
- `[hpm_clockconfig.h:PLL1_FREQ]`
- `[hpm_clockconfig.h:AUD_DIV]`
- `[hpm_config.h:HAVE_UART_DEVICE]`
- `[hpm_config.h:HAVE_UART_CONSOLE]`
- `[hpm_gpio.h:hpm_gpio_config]`
- `[hpm_gpio.h:hpm_gpio_write]`
- `[hpm_gpio.h:hpm_gpio_read]`
- `[hpm_gpio.h:hpm_gpiosetevent]`
- `[hpm_gpio.h:hpm_gpio_initialize]`
- `[hpm_gpio.h:hpm_dumpgpio]`
- `[hpm_gpio.h:gpio_pinset_t]`
- `[hpm_gpio.h:GPIO_MODE_SHIFT]`
- `[hpm_gpio.h:GPIO_MODE_MASK]`
- `[hpm_gpio.h:GPIO_INPUT]`
- `[hpm_gpio.h:GPIO_OUTPUT]`
- `[hpm_gpio.h:GPIO_PERIPH]`
- `[hpm_gpio.h:GPIO_INTERRUPT]`
- `[hpm_gpio.h:GPIO_OUTPUT_ZERO]`
- `[hpm_gpio.h:GPIO_OUTPUT_ONE]`
- `[hpm_gpio.h:GPIO_LOOP_SHIFT]`
- `[hpm_gpio.h:GPIO_LOOP_MASK]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[hpm_gpio.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[hpm_irq.c:ASSERT]` Enforces unconditional runtime assertions via `ASSERT`
- `[hpm_irq.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[hpm_lowputc.c:#error]` Compile-time configuration constraint: No CONFIG_UARTn_SERIAL_CONSOLE Setting
- `[hpm_serial.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[hpm_serial.c:#error]` Compile-time configuration constraint: I'm confused... Do we have a serial console or not?
- `[hpm_timerisr.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[hpm_clockconfig.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[hpm_clockconfig.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[hpm_gpio.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[hpm_gpio.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[hpm_ioc.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[hpm_irq.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[hpm_irq.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[hpm_irq.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[hpm_irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[hpm_irq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[hpm_irq_dispatch.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[hpm_irq_dispatch.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)

## Verification
- Run: `make test`
