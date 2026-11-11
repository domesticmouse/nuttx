# common (`nuttx/arch/arm/src/tiva/common`)

## Overview
Hardware abstraction and architecture package for `common` under `nuttx/arch/arm/src/tiva/common`, providing 2 header file(s) and 26 source file(s) (including `lmxx_tm4c_enableclks.h`, `lmxx_tm4c_enablepwr.h`, `lm4xx_tm3c_sysctrl.c`, `lmxx_tm4c_gpioirq.c`).

## Interface
- `[lmxx_tm4c_enableclks.h:tiva_enableclk]`
- `[lmxx_tm4c_enableclks.h:tiva_disableclk]`
- `[lmxx_tm4c_enableclks.h:tiva_wdt_enableclk]`
- `[lmxx_tm4c_enableclks.h:tiva_wdt_disableclk]`
- `[lmxx_tm4c_enableclks.h:tiva_wdt0_enableclk]`
- `[lmxx_tm4c_enableclks.h:tiva_wdt1_enableclk]`
- `[lmxx_tm4c_enableclks.h:tiva_wdt0_disableclk]`
- `[lmxx_tm4c_enableclks.h:tiva_wdt1_disableclk]`
- `[lmxx_tm4c_enableclks.h:tiva_gptm_enableclk]`
- `[lmxx_tm4c_enableclks.h:tiva_gptm_disableclk]`
- `[lmxx_tm4c_enableclks.h:tiva_gptm0_enableclk]`
- `[lmxx_tm4c_enableclks.h:tiva_gptm1_enableclk]`
- `[lmxx_tm4c_enablepwr.h:tiva_enablepwr]`
- `[lmxx_tm4c_enablepwr.h:tiva_disablepwr]`
- `[lmxx_tm4c_enablepwr.h:tiva_wdt_enablepwr]`
- `[lmxx_tm4c_enablepwr.h:tiva_wdt_disablepwr]`
- `[lmxx_tm4c_enablepwr.h:tiva_wdt0_enablepwr]`
- `[lmxx_tm4c_enablepwr.h:tiva_wdt1_enablepwr]`
- `[lmxx_tm4c_enablepwr.h:tiva_wdt0_disablepwr]`
- `[lmxx_tm4c_enablepwr.h:tiva_wdt1_disablepwr]`
- `[lmxx_tm4c_enablepwr.h:tiva_gptm_enablepwr]`
- `[lmxx_tm4c_enablepwr.h:tiva_gptm_disablepwr]`
- `[lm4xx_tm3c_sysctrl.c:tiva_clock_reconfigure]`
- `[lm4xx_tm3c_sysctrl.c:tiva_clock_configure]`
- `[lmxx_tm4c_gpioirq.c:tiva_gpioirqinitialize]`
- `[lmxx_tm4c_gpioirq.c:tiva_gpioirqattach]`
- `[lmxx_tm4c_gpioirq.c:tiva_gpioirqenable]`
- `[lmxx_tm4c_gpioirq.c:tiva_gpioirqdisable]`
- `[lmxx_tm4c_gpioirq.c:tiva_gpioirqclear]`
- `[lmxx_tm4c_start.c:g_idle_topstack]`

## Invariants
- `[lmxx_tm4c_gpioirq.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[tiva_adclib.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[tiva_adclib.c:#error]` Compile-time configuration constraint: Unsupported architecture reported
- `[tiva_adclow.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[tiva_adclow.c:#error]` Compile-time configuration constraint: Voltage reference selection only supported in TM4C129 parts
- `[tiva_allocateheap.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[tiva_can.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[tiva_can.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[tiva_can.c:#error]` Compile-time configuration constraint: Error reporting requires the low-priority work queue to be enabled.
- `[tiva_dumpgpio.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[tiva_dumpgpio.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[tiva_flash.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[lmxx_tm4c_enableclks.h:modifyreg32]` Performs atomic read-modify-write updates on 32-bit MMIO registers
- `[lmxx_tm4c_enablepwr.h:modifyreg32]` Performs atomic read-modify-write updates on 32-bit MMIO registers
- `[lm4xx_tm3c_sysctrl.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[lm4xx_tm3c_sysctrl.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[lm4xx_tm3c_sysctrl.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)
- `[lmxx_tm4c_gpioirq.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[lmxx_tm4c_gpioirq.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[lmxx_tm4c_gpioirq.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[lmxx_tm4c_gpioirq.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[lmxx_tm4c_gpioirq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[lmxx_tm4c_gpioirq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[tiva_adclib.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)

## Verification
- Run: `make test`
