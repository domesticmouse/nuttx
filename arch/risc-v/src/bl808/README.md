# bl808 (`nuttx/arch/risc-v/src/bl808`)

## Overview
Hardware abstraction and architecture package for `bl808` (BL808 Configuration Options; BL808 Peripheral Support) under `nuttx/arch/risc-v/src/bl808`, providing 10 header file(s) and 14 source file(s) (including `bl808_gpadc.h`, `bl808_gpio.h`, `bl808_i2c.h`, `bl808_memorymap.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/risc-v/src/bl808/hardware`, providing 10 header file(s) and 0 source file(s) (including `bl808_glb.h`, `bl808_gpadc.h`, `bl808_i2c.h`, `bl808_m0ic.h`).

## Interface
- `[bl808_gpadc.h:bl808_gpadc_init]`
- `[bl808_gpio.h:bl808_configgpio]`
- `[bl808_gpio.h:bl808_gpiowrite]`
- `[bl808_gpio.h:bl808_gpioread]`
- `[bl808_gpio.h:gpio_pinattr_t]`
- `[bl808_gpio.h:GPIO_MODE_SHIFT]`
- `[bl808_gpio.h:GPIO_MODE_MASK]`
- `[bl808_gpio.h:GPIO_INPUT]`
- `[bl808_gpio.h:GPIO_OUTPUT]`
- `[bl808_gpio.h:GPIO_PUPD_SHIFT]`
- `[bl808_gpio.h:GPIO_PUPD_MASK]`
- `[bl808_gpio.h:GPIO_FLOAT]`
- `[bl808_gpio.h:GPIO_PULLUP]`
- `[bl808_gpio.h:GPIO_PULLDOWN]`
- `[bl808_gpio.h:GPIO_DRV_SHIFT]`
- `[bl808_gpio.h:GPIO_DRV_MASK]`
- `[bl808_gpio.h:GPIO_DRV_0]`
- `[bl808_i2c.h:bl808_i2cbus_initialize]`
- `[bl808_i2c.h:bl808_i2cbus_uninitialize]`
- `[bl808_memorymap.h:BL808_IDLESTACK_BASE]`
- `[bl808_mm_init.h:bl808_kernel_mappings]`
- `[bl808_mm_init.h:bl808_mm_init]`
- `[bl808_serial.h:bl808_earlyserialinit]`
- `[bl808_serial.h:bl808_serialinit]`
- `[bl808_spi.h:bl808_spibus_initialize]`
- `[bl808_timer.h:bl808_timer_init]`
- `[bl808_wdt.h:bl808_wdt_init]`
- `[bl808_allocateheap.c:up_allocate_kheap]`
- `[bl808_gpadc.c:bl808_gpadc_get_count]`
- `[bl808_gpadc.c:bl808_gpadc_init]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[bl808_gpio.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[bl808_irq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[bl808_irq.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[bl808_mm_init.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[bl808_pgalloc.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[bl808_serial.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[bl808_start.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[bl808_start.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[bl808_timerisr.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[bl808_gpadc.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[bl808_gpadc.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[bl808_gpadc.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[bl808_gpadc.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[bl808_gpadc.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[bl808_gpio.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[bl808_gpio.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[bl808_gpio.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[bl808_i2c.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[bl808_i2c.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[bl808_i2c.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[bl808_i2c.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)

## Verification
- Run: `make test`
