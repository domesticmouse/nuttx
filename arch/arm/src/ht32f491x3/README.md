# ht32f491x3 (`nuttx/arch/arm/src/ht32f491x3`)

## Overview
Hardware abstraction and architecture package for `ht32f491x3` (HT32F491x3 Configuration Options; Peripheral Support) under `nuttx/arch/arm/src/ht32f491x3`, providing 7 header file(s) and 8 source file(s) (including `chip.h`, `ht32f491x3_config.h`, `ht32f491x3_gpio.h`, `ht32f491x3_lowputc.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/ht32f491x3/hardware`, providing 7 header file(s) and 0 source file(s) (including `ht32f491x3_crm.h`, `ht32f491x3_flash.h`, `ht32f491x3_gpio.h`, `ht32f491x3_memorymap.h`).

## Interface
- `[chip.h:ARMV7M_PERIPHERAL_INTERRUPTS]`
- `[ht32f491x3_config.h:HAVE_UART]`
- `[ht32f491x3_config.h:HAVE_CONSOLE]`
- `[ht32f491x3_gpio.h:ht32f491x3_gpioconfig]`
- `[ht32f491x3_gpio.h:ht32f491x3_gpiowrite]`
- `[ht32f491x3_gpio.h:ht32f491x3_gpioread]`
- `[ht32f491x3_gpio.h:HT32_GPIO_MODE_INPUT]`
- `[ht32f491x3_gpio.h:HT32_GPIO_MODE_OUTPUT]`
- `[ht32f491x3_gpio.h:HT32_GPIO_MODE_ALTFN]`
- `[ht32f491x3_gpio.h:HT32_GPIO_MODE_ANALOG]`
- `[ht32f491x3_gpio.h:HT32_GPIO_DRIVE_LOW]`
- `[ht32f491x3_gpio.h:HT32_GPIO_DRIVE_MEDIUM]`
- `[ht32f491x3_gpio.h:HT32_GPIO_DRIVE_HIGH]`
- `[ht32f491x3_gpio.h:HT32_GPIO_PULL_NONE]`
- `[ht32f491x3_gpio.h:HT32_GPIO_PULL_UP]`
- `[ht32f491x3_gpio.h:HT32_GPIO_PULL_DOWN]`
- `[ht32f491x3_lowputc.h:ht32f491x3_lowsetup]`
- `[ht32f491x3_lowputc.h:ht32f491x3_usart_config]`
- `[ht32f491x3_pwm.h:ht32f491x3_pwminitialize]`
- `[ht32f491x3_serial.h:arm_earlyserialinit]`
- `[ht32f491x3_serial.h:arm_serialinit]`
- `[ht32f491x3_serial.h:ht32f491x3_usart_pins]`
- `[ht32f491x3_start.h:ht32f491x3_clockconfig]`
- `[ht32f491x3_start.h:ht32f491x3_boardinitialize]`
- `[arm_vectors.c:start]`
- `[arm_vectors.c:IDLE_STACK]`
- `[ht32f491x3_gpio.c:ht32f491x3_gpioconfig]`
- `[ht32f491x3_gpio.c:ht32f491x3_gpiowrite]`
- `[ht32f491x3_gpio.c:ht32f491x3_gpioread]`
- `[ht32f491x3_irq.c:up_irqinitialize]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[arm_vectors.c:#error]` Compile-time configuration constraint: Unsupported HT32F491x3 device
- `[ht32f491x3_irq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[ht32f491x3_irq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[ht32f491x3_irq.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[ht32f491x3_pwm.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[ht32f491x3_pwm.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[ht32f491x3_serial.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[ht32f491x3_timerisr.c:#error]` Compile-time configuration constraint: HT32_SYSTICK_RELOAD exceeds the SysTick reload field

## Side Effects
- `[ht32f491x3_gpio.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[ht32f491x3_gpio.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[ht32f491x3_gpio.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[ht32f491x3_irq.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[ht32f491x3_irq.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[ht32f491x3_irq.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[ht32f491x3_irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[ht32f491x3_irq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[ht32f491x3_lowputc.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[ht32f491x3_lowputc.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[ht32f491x3_lowputc.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[ht32f491x3_pwm.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)

## Verification
- Run: `make test`
