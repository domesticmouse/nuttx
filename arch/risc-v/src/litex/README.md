# litex (`nuttx/arch/risc-v/src/litex`)

## Overview
Hardware abstraction and architecture package for `litex` (LITEX Configuration Options; LITEX Peripheral Support) under `nuttx/arch/risc-v/src/litex`, providing 11 header file(s) and 18 source file(s) (including `chip.h`, `litex.h`, `litex_clockconfig.h`, `litex_config.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/risc-v/src/litex/hardware`, providing 7 header file(s) and 0 source file(s) (including `litex_clint.h`, `litex_emac.h`, `litex_memorymap.h`, `litex_plic.h`).

## Interface
- `[litex_clockconfig.h:litex_get_hfclk]`
- `[litex_clockconfig.h:litex_clockconfig]`
- `[litex_config.h:HAVE_UART_DEVICE]`
- `[litex_config.h:HAVE_SERIAL_CONSOLE]`
- `[litex_ctrl.h:litex_ctrl_write_scratch]`
- `[litex_ctrl.h:litex_ctrl_read_scratch]`
- `[litex_ctrl.h:litex_ctrl_read_bus_error]`
- `[litex_gpio.h:litex_gpio_config]`
- `[litex_gpio.h:litex_gpio_write]`
- `[litex_gpio.h:litex_gpio_read]`
- `[litex_gpio.h:litex_gpio_irq_enable]`
- `[litex_gpio.h:litex_gpio_irq_config]`
- `[litex_gpio.h:litex_gpio_irq_disable]`
- `[litex_gpio.h:gpio_isr_config_s]`
- `[litex_gpio.h:gpio_pinattr_t]`
- `[litex_gpio.h:gpio_intrtype_t]`
- `[litex_gpio.h:GPIO_PINMODE_INPUT]`
- `[litex_gpio.h:GPIO_PINMODE_OUTPUT]`
- `[litex_gpio.h:GPIO_ISR_NONE]`
- `[litex_gpio.h:GPIO_ISR_RISING_EDGE]`
- `[litex_gpio.h:GPIO_ISR_FALLING_EDGE]`
- `[litex_gpio.h:GPIO_ISR_BOTH_EDGES]`
- `[litex_lowputc.h:litex_lowsetup]`
- `[litex_memorymap.h:LITEX_IDLESTACK_BASE]`
- `[litex_memorymap.h:LITEX_IDLESTACK_TOP]`
- `[litex_mm_init.h:litex_kernel_mappings]`
- `[litex_mm_init.h:litex_mm_init]`
- `[litex_pwm.h:litex_pwminitialize]`
- `[litex_sdio.h:litex_sdio_get_card_detect]`
- `[litex_sdio.h:litex_sdio_set_card_isr]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[litex_arch_alarm.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[litex_emac.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[litex_emac.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[litex_emac.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[litex_emac.c:#error]` Compile-time configuration constraint: Work queue support is required
- `[litex_gpio.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[litex_irq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[litex_irq.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[litex_irq_dispatch.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[litex_mm_init.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[litex_mm_init.c:#error]` Compile-time configuration constraint: No valid MMU defined.
- `[litex_pgalloc.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[litex_ctrl.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[litex_ctrl.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[litex_emac.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[litex_emac.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[litex_emac.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[litex_emac.c:putreg8]` Mutates 8-bit memory-mapped I/O (MMIO) hardware registers (`putreg8`)
- `[litex_emac.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[litex_emac.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[litex_emac.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[litex_gpio.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[litex_gpio.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[litex_gpio.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)

## Verification
- Run: `make test`
