# mx8mp (`nuttx/arch/arm/src/mx8mp`)

## Overview
Hardware abstraction and architecture package for `mx8mp` (i.MX8MP Configuration Options; i.MX8MP Peripheral Selection) under `nuttx/arch/arm/src/mx8mp`, providing 16 header file(s) and 18 source file(s) (including `chip.h`, `mx8mp_ccm.h`, `mx8mp_clockconfig.h`, `mx8mp_config.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/mx8mp/hardware`, providing 10 header file(s) and 0 source file(s) (including `mx8mp_ccm.h`, `mx8mp_ecspi.h`, `mx8mp_gpc.h`, `mx8mp_gpio.h`).

## Interface
- `[chip.h:ARMV7M_PERIPHERAL_INTERRUPTS]`
- `[mx8mp_ccm.h:mx8mp_ccm_get_root_clock]`
- `[mx8mp_ccm.h:mx8mp_ccm_get_clock]`
- `[mx8mp_ccm.h:mx8mp_ccm_configure_clock]`
- `[mx8mp_ccm.h:mx8mp_ccm_enable_clock]`
- `[mx8mp_ccm.h:mx8mp_ccm_gate_clock]`
- `[mx8mp_ccm.h:mx8mp_ccm_gate_pll]`
- `[mx8mp_ccm.h:mx8mp_ccm_configure_pll]`
- `[mx8mp_clockconfig.h:mx8mp_clockconfig]`
- `[mx8mp_config.h:HAVE_UART_CONSOLE]`
- `[mx8mp_ecspi.h:mx8mp_spibus_initialize]`
- `[mx8mp_ecspi.h:mx8mp_spi1_select]`
- `[mx8mp_ecspi.h:mx8mp_spi1_status]`
- `[mx8mp_ecspi.h:mx8mp_spi1_cmddata]`
- `[mx8mp_ecspi.h:mx8mp_spi2_select]`
- `[mx8mp_ecspi.h:mx8mp_spi2_status]`
- `[mx8mp_ecspi.h:mx8mp_spi2_cmddata]`
- `[mx8mp_ecspi.h:mx8mp_spi3_select]`
- `[mx8mp_ecspi.h:mx8mp_spi3_status]`
- `[mx8mp_ecspi.h:mx8mp_spi3_cmddata]`
- `[mx8mp_gpio.h:mx8mp_gpio_config]`
- `[mx8mp_gpio.h:mx8mp_gpio_write]`
- `[mx8mp_gpio.h:mx8mp_gpio_read]`
- `[mx8mp_gpio.h:mx8mp_gpio_irq_initialize]`
- `[mx8mp_gpio.h:mx8mp_gpio_configure_irq]`
- `[mx8mp_gpio.h:mx8mp_gpio_irq_enable]`
- `[mx8mp_gpio.h:mx8mp_gpio_irq_disable]`
- `[mx8mp_gpio.h:gpio_pinset_t]`
- `[mx8mp_gpio.h:GPIO_MODE_SHIFT]`
- `[mx8mp_gpio.h:GPIO_MODE_MASK]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[mx8mp_config.h:#error]` Compile-time guard: MPU is required for proper behavior
- `[mx8mp_mpuinit.h:#error]` Compile-time guard: not implemented
- `[mx8mp_allocateheap.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[mx8mp_ecspi.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[mx8mp_ecspi.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[mx8mp_gpio.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[mx8mp_i2c.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[mx8mp_ipc.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[mx8mp_irq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[mx8mp_irq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[mx8mp_irq.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[mx8mp_irq.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)

## Side Effects
- `[mx8mp_ccm.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[mx8mp_ccm.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[mx8mp_clockconfig.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[mx8mp_clrpend.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[mx8mp_ecspi.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[mx8mp_ecspi.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[mx8mp_ecspi.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[mx8mp_ecspi.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[mx8mp_gpio.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[mx8mp_gpio.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[mx8mp_gpio.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[mx8mp_gpio.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)

## Verification
- Run: `make test`
