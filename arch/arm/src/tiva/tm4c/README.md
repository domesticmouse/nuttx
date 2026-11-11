# tm4c (`nuttx/arch/arm/src/tiva/tm4c`)

## Overview
Hardware abstraction and architecture package for `tm4c` under `nuttx/arch/arm/src/tiva/tm4c`, providing 1 header file(s) and 3 source file(s) (including `tm4c_gpio.h`, `tm4c129_sysctrl.c`, `tm4c_ethernet.c`, `tm4c_gpio.c`).

## Interface
- `[tm4c_gpio.h:pinconfig_t]`
- `[tm4c_gpio.h:GPIO_FUNC_SHIFT]`
- `[tm4c_gpio.h:GPIO_FUNC_MASK]`
- `[tm4c_gpio.h:GPIO_FUNC_INPUT]`
- `[tm4c_gpio.h:GPIO_FUNC_OUTPUT]`
- `[tm4c_gpio.h:GPIO_FUNC_ODINPUT]`
- `[tm4c_gpio.h:GPIO_FUNC_ODOUTPUT]`
- `[tm4c_gpio.h:GPIO_FUNC_PFODIO]`
- `[tm4c_gpio.h:GPIO_FUNC_PFINPUT]`
- `[tm4c_gpio.h:GPIO_FUNC_PFOUTPUT]`
- `[tm4c_gpio.h:GPIO_FUNC_PFIO]`
- `[tm4c_gpio.h:GPIO_FUNC_ANINPUT]`
- `[tm4c_gpio.h:GPIO_FUNC_ANIO]`
- `[tm4c129_sysctrl.c:tiva_clock_reconfigure]`
- `[tm4c129_sysctrl.c:tiva_clock_configure]`
- `[tm4c_ethernet.c:tiva_ethinitialize]`
- `[tm4c_ethernet.c:arm_netinitialize]`
- `[tm4c_ethernet.c:arch_phy_irq]`
- `[tm4c_gpio.c:tiva_gpiobaseaddress]`
- `[tm4c_gpio.c:tiva_configgpio]`
- `[tm4c_gpio.c:tiva_gpiowrite]`
- `[tm4c_gpio.c:tiva_gpioread]`
- `[tm4c_gpio.c:tiva_gpio_lockport]`
- `[CMakeLists.txt:target_sources]`

## Invariants
- `[tm4c129_sysctrl.c:#error]` Compile-time configuration constraint: Crystal frequency is not supported
- `[tm4c_ethernet.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[tm4c_ethernet.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[tm4c_ethernet.c:#error]` Compile-time configuration constraint: Logic to support multiple Ethernet interfaces is incomplete
- `[tm4c_gpio.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[tm4c_gpio.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)

## Side Effects
- `[tm4c129_sysctrl.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[tm4c129_sysctrl.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[tm4c_ethernet.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[tm4c_ethernet.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[tm4c_ethernet.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[tm4c_ethernet.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[tm4c_ethernet.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[tm4c_gpio.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[tm4c_gpio.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[tm4c_gpio.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)

## Verification
- Run: `make test`
