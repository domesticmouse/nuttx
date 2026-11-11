# ab32vg1 (`nuttx/arch/risc-v/src/ab32vg1`)

## Overview
Hardware abstraction and architecture package for `ab32vg1` (AB32VG1 Configuration Options; AB32VG1 Peripheral Support) under `nuttx/arch/risc-v/src/ab32vg1`, providing 4 header file(s) and 10 source file(s) (including `ab32vg1.h`, `ab32vg1_gpio.h`, `ab32vg1_lowputc.h`, `chip.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/risc-v/src/ab32vg1/hardware`, providing 6 header file(s) and 0 source file(s) (including `ab32vg1_clk.h`, `ab32vg1_gpio.h`, `ab32vg1_memorymap.h`, `ab32vg1_pic.h`).

## Interface
- `[ab32vg1.h:ab32vg1_clockconfig]`
- `[ab32vg1.h:ab32vg1_lowsetup]`
- `[ab32vg1.h:ab32vg1_boardinitialize]`
- `[ab32vg1.h:ab32vg1_dispatch_trap]`
- `[ab32vg1.h:AB32VG1_IDLESTACK_BASE]`
- `[ab32vg1.h:AB32VG1_IDLESTACK_TOP]`
- `[ab32vg1.h:AB32VG1_SYSCLK_FREQUENCY]`
- `[ab32vg1_gpio.h:ab32vg1_gpiowrite]`
- `[ab32vg1_gpio.h:ab32vg1_gpioread]`
- `[ab32vg1_gpio.h:gpio_pinset_t]`
- `[ab32vg1_gpio.h:GPIO_PIN_SHIFT]`
- `[ab32vg1_gpio.h:GPIO_PIN_MASK]`
- `[ab32vg1_gpio.h:GPIO_PIN]`
- `[ab32vg1_gpio.h:GPIO_PORT_SHIFT]`
- `[ab32vg1_gpio.h:GPIO_PORT_MASK]`
- `[ab32vg1_gpio.h:GPIO_PORTA]`
- `[ab32vg1_gpio.h:GPIO_PORTB]`
- `[ab32vg1_gpio.h:GPIO_PORTE]`
- `[ab32vg1_gpio.h:GPIO_PORTF]`
- `[ab32vg1_gpio.h:GPIO_OUTPUT]`
- `[ab32vg1_gpio.h:GPIO_INPUT]`
- `[ab32vg1_gpio.h:GPIO_VALUE_ONE]`
- `[ab32vg1_lowputc.h:ab32vg1_uart0_configure]`
- `[ab32vg1_allocateheap.c:up_allocate_heap]`
- `[ab32vg1_allocateheap.c:riscv_addregion]`
- `[ab32vg1_clockconfig.c:ab32vg1_clockconfig]`
- `[ab32vg1_gpio.c:ab32vg1_configgpio]`
- `[ab32vg1_gpio.c:ab32vg1_gpiowrite]`
- `[ab32vg1_gpio.c:ab32vg1_gpioread]`
- `[ab32vg1_idle.c:up_idle]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[ab32vg1_allocateheap.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[ab32vg1_clockconfig.c:#error]` Compile-time configuration constraint: CONFIG_AB32VG1_SYSCLK_MHZ must divide 240 MHz
- `[ab32vg1_gpio.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[ab32vg1_irq.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[ab32vg1_serial.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[ab32vg1_serial.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[ab32vg1_serial.c:#error]` Compile-time configuration constraint: The serial driver requires CONFIG_AB32VG1_UART0
- `[ab32vg1_systemreset.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)

## Side Effects
- `[ab32vg1_clockconfig.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[ab32vg1_clockconfig.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[ab32vg1_clockconfig.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[ab32vg1_gpio.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[ab32vg1_gpio.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[ab32vg1_gpio.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[ab32vg1_idle.c:nxsched_process_timer]` Advances the NuttX kernel system tick and scheduler timer state (`nxsched_process_timer`)
- `[ab32vg1_irq.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[ab32vg1_irq.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[ab32vg1_irq.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[ab32vg1_irq.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[ab32vg1_irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)

## Verification
- Run: `make test`
