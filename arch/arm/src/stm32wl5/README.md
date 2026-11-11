# stm32wl5 (`nuttx/arch/arm/src/stm32wl5`)

## Overview
Hardware abstraction and architecture package for `stm32wl5` (STM32WL5 Configuration Options) under `nuttx/arch/arm/src/stm32wl5`, providing 14 header file(s) and 14 source file(s) (including `chip.h`, `stm32.h`, `stm32wl5_exti.h`, `stm32wl5_flash.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/stm32wl5/hardware`, providing 11 header file(s) and 0 source file(s) (including `stm32_rcc.h`, `stm32wl5_exti.h`, `stm32wl5_flash.h`, `stm32wl5_gpio.h`).

## Interface
- `[chip.h:ARMV7M_PERIPHERAL_INTERRUPTS]`
- `[chip.h:ARMV7M_DCACHE_LINESIZE]`
- `[chip.h:ARMV7M_ICACHE_LINESIZE]`
- `[stm32.h:stm32_spidev_initialize]`
- `[stm32wl5_exti.h:stm32_gpiosetevent]`
- `[stm32wl5_exti.h:stm32_exti_alarm]`
- `[stm32wl5_exti.h:stm32_exti_wakeup]`
- `[stm32wl5_exti.h:stm32_exti_comp]`
- `[stm32wl5_flash.h:stm32_flash_lock]`
- `[stm32wl5_flash.h:stm32_flash_unlock]`
- `[stm32wl5_flash.h:stm32_flash_user_optbytes]`
- `[stm32wl5_gpio.h:stm32_configgpio]`
- `[stm32wl5_gpio.h:stm32_unconfiggpio]`
- `[stm32wl5_gpio.h:stm32_gpiowrite]`
- `[stm32wl5_gpio.h:stm32_gpioread]`
- `[stm32wl5_gpio.h:stm32_gpiosetevent]`
- `[stm32wl5_gpio.h:stm32_dumpgpio]`
- `[stm32wl5_gpio.h:stm32_gpioinit]`
- `[stm32wl5_gpio.h:GPIO_MODE_SHIFT]`
- `[stm32wl5_gpio.h:GPIO_MODE_MASK]`
- `[stm32wl5_gpio.h:GPIO_INPUT]`
- `[stm32wl5_gpio.h:GPIO_OUTPUT]`
- `[stm32wl5_gpio.h:GPIO_ALT]`
- `[stm32wl5_gpio.h:GPIO_ANALOG]`
- `[stm32wl5_gpio.h:GPIO_PUPD_SHIFT]`
- `[stm32wl5_gpio.h:GPIO_PUPD_MASK]`
- `[stm32wl5_gpio.h:GPIO_FLOAT]`
- `[stm32wl5_gpio.h:GPIO_PULLUP]`
- `[stm32wl5_gpio.h:GPIO_PULLDOWN]`
- `[stm32wl5_gpio.h:GPIO_AF_SHIFT]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[stm32wl5_gpio.h:#error]` Compile-time guard: Unsupported STM32WL5 chip
- `[stm32wl5_allocateheap.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[stm32wl5_allocateheap.c:#error]` Compile-time configuration constraint: You need more memory manager regions to support selected heap components
- `[stm32wl5_flash.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[stm32wl5_gpio.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[stm32wl5_ipcc.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[stm32wl5_irq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[stm32wl5_irq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[stm32wl5_irq.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[stm32wl5_irq.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[stm32wl5_lse.c:static_assert]` Enforces compile-time size and alignment invariants via `static_assert`
- `[stm32wl5_lse.c:#error]` Compile-time configuration constraint: Invalid LSE drive capability setting

## Side Effects
- `[stm32wl5_rcc.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[stm32wl5_rcc.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[stm32wl5_exti_gpio.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[stm32wl5_exti_gpio.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[stm32wl5_exti_gpio.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[stm32wl5_exti_gpio.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[stm32wl5_exti_gpio.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[stm32wl5_exti_gpio.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[stm32wl5_flash.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[stm32wl5_flash.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[stm32wl5_flash.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[stm32wl5_gpio.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)

## Verification
- Run: `make test`
