# lm (`nuttx/arch/arm/src/tiva/lm`)

## Overview
Hardware abstraction and architecture package for `lm` under `nuttx/arch/arm/src/tiva/lm`, providing 2 header file(s) and 3 source file(s) (including `lm3s_gpio.h`, `lm4f_gpio.h`, `lm3s_ethernet.c`, `lm3s_gpio.c`).

## Interface
- `[lm3s_gpio.h:pinconfig_t]`
- `[lm3s_gpio.h:GPIO_FUNC_SHIFT]`
- `[lm3s_gpio.h:GPIO_FUNC_MASK]`
- `[lm3s_gpio.h:GPIO_FUNC_INPUT]`
- `[lm3s_gpio.h:GPIO_FUNC_OUTPUT]`
- `[lm3s_gpio.h:GPIO_FUNC_ODINPUT]`
- `[lm3s_gpio.h:GPIO_FUNC_ODOUTPUT]`
- `[lm3s_gpio.h:GPIO_FUNC_PFODIO]`
- `[lm3s_gpio.h:GPIO_FUNC_PFINPUT]`
- `[lm3s_gpio.h:GPIO_FUNC_PFOUTPUT]`
- `[lm3s_gpio.h:GPIO_FUNC_PFIO]`
- `[lm3s_gpio.h:GPIO_FUNC_ANINPUT]`
- `[lm3s_gpio.h:GPIO_FUNC_ANIO]`
- `[lm4f_gpio.h:pinconfig_t]`
- `[lm4f_gpio.h:GPIO_FUNC_SHIFT]`
- `[lm4f_gpio.h:GPIO_FUNC_MASK]`
- `[lm4f_gpio.h:GPIO_FUNC_INPUT]`
- `[lm4f_gpio.h:GPIO_FUNC_OUTPUT]`
- `[lm4f_gpio.h:GPIO_FUNC_ODINPUT]`
- `[lm4f_gpio.h:GPIO_FUNC_ODOUTPUT]`
- `[lm4f_gpio.h:GPIO_FUNC_PFODIO]`
- `[lm4f_gpio.h:GPIO_FUNC_PFINPUT]`
- `[lm4f_gpio.h:GPIO_FUNC_PFOUTPUT]`
- `[lm4f_gpio.h:GPIO_FUNC_PFIO]`
- `[lm4f_gpio.h:GPIO_FUNC_ANINPUT]`
- `[lm4f_gpio.h:GPIO_FUNC_ANIO]`
- `[lm3s_ethernet.c:arm_netinitialize]`
- `[lm3s_gpio.c:tiva_gpiobaseaddress]`
- `[lm3s_gpio.c:tiva_configgpio]`
- `[lm3s_gpio.c:tiva_gpiowrite]`

## Invariants
- `[lm3s_ethernet.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[lm3s_ethernet.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[lm3s_ethernet.c:#error]` Compile-time configuration constraint: Work queue support is required in this configuration (CONFIG_SCHED_WORKQUEUE)
- `[lm3s_gpio.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[lm3s_gpio.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[lm4f_gpio.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[lm4f_gpio.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)

## Side Effects
- `[lm3s_ethernet.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[lm3s_ethernet.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[lm3s_ethernet.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[lm3s_ethernet.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[lm3s_ethernet.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[lm3s_gpio.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[lm3s_gpio.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[lm3s_gpio.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[lm4f_gpio.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[lm4f_gpio.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[lm4f_gpio.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)

## Verification
- Run: `make test`
