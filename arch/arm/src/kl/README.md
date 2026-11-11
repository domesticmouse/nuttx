# kl (`nuttx/arch/arm/src/kl`)

## Overview
Hardware abstraction and architecture package for `kl` (Kinetis Configuration Options; Kinetis Peripheral Support) under `nuttx/arch/arm/src/kl`, providing 11 header file(s) and 15 source file(s) (including `chip.h`, `kl_clockconfig.h`, `kl_config.h`, `kl_dma.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/kl/hardware`, providing 16 header file(s) and 0 source file(s) (including `k25z128_pinmux.h`, `kl_fmc.h`, `kl_gpio.h`, `kl_i2c.h`).

## Interface
- `[chip.h:ARMV6M_PERIPHERAL_INTERRUPTS]`
- `[kl_clockconfig.h:kl_clockconfig]`
- `[kl_config.h:HAVE_UART_DEVICE]`
- `[kl_config.h:HAVE_SERIAL_CONSOLE]`
- `[kl_dma.h:kl_dmainitilaize]`
- `[kl_dma.h:kl_dmachannel]`
- `[kl_dma.h:kl_dmafree]`
- `[kl_dma.h:kl_dmarxsetup]`
- `[kl_dma.h:kl_dmastart]`
- `[kl_dma.h:kl_dmastop]`
- `[kl_dma.h:kl_dmasample]`
- `[kl_dma.h:kl_dmadump]`
- `[kl_dma.h:kl_dmaglobalregs_s]`
- `[kl_dma.h:kl_dmachanregs_s]`
- `[kl_dma.h:kl_dmaregs_s]`
- `[kl_dma.h:DMA_HANDLE]`
- `[kl_gpio.h:kl_configgpio]`
- `[kl_gpio.h:kl_gpiowrite]`
- `[kl_gpio.h:kl_gpioread]`
- `[kl_gpio.h:kl_gpioirqattach]`
- `[kl_gpio.h:kl_gpioirqenable]`
- `[kl_gpio.h:kl_gpioirqdisable]`
- `[kl_gpio.h:gpio_cfgset_t]`
- `[kl_gpio.h:_PIN_MODE_SHIFT]`
- `[kl_gpio.h:_PIN_MODE_MASK]`
- `[kl_gpio.h:_PIN_OPTIONS_SHIFT]`
- `[kl_gpio.h:_PIN_OPTIONS_MASK]`
- `[kl_gpio.h:PIN_MODE_ANALOG]`
- `[kl_gpio.h:PIN_MODE_GPIO]`
- `[kl_gpio.h:PIN_MODE_ALT2]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[kl_pwm.h:#error]` Compile-time guard: CONFIG_KL_TPM0_CHANNEL must be provided
- `[kl_dumpgpio.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[kl_dumpgpio.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[kl_dumpgpio.c:#error]` Compile-time configuration constraint: Additional support required for this number of GPIOs
- `[kl_gpio.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[kl_gpioirq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[kl_gpioirq.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[kl_gpioirq.c:#error]` Compile-time configuration constraint: Kinetis KL25 only supports interrupt on PORTA or PORTD
- `[kl_idle.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[kl_irq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[kl_irq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[kl_irq.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates

## Side Effects
- `[kl_clockconfig.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[kl_clockconfig.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[kl_clockconfig.c:putreg8]` Mutates 8-bit memory-mapped I/O (MMIO) hardware registers (`putreg8`)
- `[kl_dumpgpio.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[kl_gpio.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[kl_gpio.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[kl_gpioirq.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[kl_gpioirq.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[kl_gpioirq.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[kl_gpioirq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[kl_idle.c:nxsched_process_timer]` Advances the NuttX kernel system tick and scheduler timer state (`nxsched_process_timer`)
- `[kl_irq.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)

## Verification
- Run: `make test`
