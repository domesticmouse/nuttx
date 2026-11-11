# pic32mx (`nuttx/arch/mips/src/pic32mx`)

## Overview
Hardware abstraction and architecture package for `pic32mx` (PIC32MX Configuration Options; PIC32MX Peripheral Support) under `nuttx/arch/mips/src/pic32mx`, providing 31 header file(s) and 12 source file(s) (including `chip.h`, `excptmacros.h`, `pic32mx.h`, `pic32mx_adc.h`).

## Interface
- `[pic32mx.h:pic32mx_lowinit]`
- `[pic32mx.h:pic32mx_consoleinit]`
- `[pic32mx.h:pic32mx_uartreset]`
- `[pic32mx.h:pic32mx_uartconfigure]`
- `[pic32mx.h:pic32mx_boardinitialize]`
- `[pic32mx.h:pic32mx_decodeirq]`
- `[pic32mx.h:pic32mx_exception]`
- `[pic32mx.h:pic32mx_configgpio]`
- `[pic32mx.h:pic32mx_gpiowrite]`
- `[pic32mx.h:pic32mx_gpioread]`
- `[pic32mx.h:pic32mx_gpioirqinitialize]`
- `[pic32mx.h:pic32mx_gpioattach]`
- `[pic32mx.h:pic32mx_gpioirqenable]`
- `[pic32mx.h:pic32mx_gpioirqdisable]`
- `[pic32mx.h:pic32mx_dumpgpio]`
- `[pic32mx.h:pic32mx_spibus_initialize]`
- `[pic32mx.h:pic32mx_spi1select]`
- `[pic32mx.h:pic32mx_spi1status]`
- `[pic32mx.h:pic32mx_spi1cmddata]`
- `[pic32mx.h:pic32mx_spi2select]`
- `[pic32mx.h:pic32mx_spi2status]`
- `[pic32mx.h:pic32mx_spi2cmddata]`
- `[pic32mx.h:pic32mx_spi3select]`
- `[pic32mx.h:pic32mx_spi3status]`
- `[pic32mx.h:pic32mx_spi3cmddata]`
- `[pic32mx.h:pic32mx_dmainitilaize]`
- `[pic32mx.h:pic32mx_dmachannel]`
- `[pic32mx.h:pic32mx_dmafree]`
- `[pic32mx.h:pic32mx_dmarxsetup]`
- `[pic32mx.h:pic32mx_dmastart]`

## Invariants
- `[pic32mx_config.h:#error]` Compile-time guard: CONFIG_PIC32MX_CTPRIO is too small
- `[pic32mx_int.h:#error]` Compile-time guard: Unknown PIC32MX family
- `[pic32mx_memorymap.h:#error]` Compile-time guard: Memory map unknown for this PIC32 chip
- `[pic32mx_decodeirq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[pic32mx_ethernet.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[pic32mx_ethernet.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[pic32mx_ethernet.c:#error]` Compile-time configuration constraint: Work queue support is required in this configuration (CONFIG_SCHED_WORKQUEUE)
- `[pic32mx_gpio.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[pic32mx_gpioirq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[pic32mx_gpioirq.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[pic32mx_irq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[pic32mx_irq.c:#error]` Compile-time configuration constraint: Multi-vectors not supported

## Side Effects
- `[pic32mx_decodeirq.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[pic32mx_ethernet.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[pic32mx_ethernet.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[pic32mx_ethernet.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[pic32mx_ethernet.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[pic32mx_ethernet.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[pic32mx_ethernet.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)
- `[pic32mx_gpio.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[pic32mx_gpio.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[pic32mx_gpioirq.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[pic32mx_gpioirq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[pic32mx_irq.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)

## Verification
- Run: `make test`
