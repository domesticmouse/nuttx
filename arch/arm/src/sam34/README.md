# sam34 (`nuttx/arch/arm/src/sam34`)

## Overview
Hardware abstraction and architecture package for `sam34` (AT91SAM3/4 Configuration Options; AT91SAM3/4 Peripheral Support) under `nuttx/arch/arm/src/sam34`, providing 37 header file(s) and 40 source file(s) (including `chip.h`, `sam3u_gpio.h`, `sam3u_periphclks.h`, `sam3x_gpio.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/sam34/hardware`, providing 63 header file(s) and 0 source file(s) (including `sam3u_memorymap.h`, `sam3u_pinmap.h`, `sam3u_pio.h`, `sam3x_memorymap.h`).

## Interface
- `[chip.h:ARMV7M_PERIPHERAL_INTERRUPTS]`
- `[sam3u_gpio.h:gpio_pinset_t]`
- `[sam3u_gpio.h:GPIO_MODE_SHIFT]`
- `[sam3u_gpio.h:GPIO_MODE_MASK]`
- `[sam3u_gpio.h:GPIO_INPUT]`
- `[sam3u_gpio.h:GPIO_OUTPUT]`
- `[sam3u_gpio.h:GPIO_PERIPHA]`
- `[sam3u_gpio.h:GPIO_PERIPHB]`
- `[sam3u_gpio.h:GPIO_CFG_SHIFT]`
- `[sam3u_gpio.h:GPIO_CFG_MASK]`
- `[sam3u_gpio.h:GPIO_CFG_DEFAULT]`
- `[sam3u_gpio.h:GPIO_CFG_PULLUP]`
- `[sam3u_gpio.h:GPIO_CFG_DEGLITCH]`
- `[sam3u_gpio.h:GPIO_CFG_OPENDRAIN]`
- `[sam3u_periphclks.h:sam_enableperipheral]`
- `[sam3u_periphclks.h:sam_disableperipheral]`
- `[sam3u_periphclks.h:sam_supc_enableclk]`
- `[sam3u_periphclks.h:sam_rstc_enableclk]`
- `[sam3u_periphclks.h:sam_rtc_enableclk]`
- `[sam3u_periphclks.h:sam_rtt_enableclk]`
- `[sam3u_periphclks.h:sam_wdt_enableclk]`
- `[sam3u_periphclks.h:sam_pmc_enableclk]`
- `[sam3u_periphclks.h:sam_eefc0_enableclk]`
- `[sam3u_periphclks.h:sam_eefc1_enableclk]`
- `[sam3u_periphclks.h:sam_uart0_enableclk]`
- `[sam3u_periphclks.h:sam_smc_enableclk]`
- `[sam3x_gpio.h:gpio_pinset_t]`
- `[sam3x_gpio.h:GPIO_MODE_SHIFT]`
- `[sam3x_gpio.h:GPIO_MODE_MASK]`
- `[sam3x_gpio.h:GPIO_INPUT]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[sam_aes.h:#error]` Compile-time guard: Unknown chip for AES
- `[sam_gpio.h:#error]` Compile-time guard: Unrecognized SAM architecture
- `[sam_periphclks.h:#error]` Compile-time guard: Unknown SAM chip
- `[sam4cm_freerun.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[sam4cm_freerun.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[sam4cm_oneshot.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[sam4cm_oneshot.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[sam4cm_oneshot_lowerhalf.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[sam4cm_oneshot_lowerhalf.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[sam4cm_tc.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[sam4cm_tc.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[sam4cm_tickless.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[sam3u_periphclks.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[sam3x_periphclks.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[sam4cm_periphclks.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[sam4e_periphclks.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[sam4s_periphclks.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[sam4cm_cpuidlestack.c:nxsched_process_timer]` Advances the NuttX kernel system tick and scheduler timer state (`nxsched_process_timer`)
- `[sam4cm_cpuindex.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[sam4cm_cpustart.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[sam4cm_cpustart.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[sam4cm_cpustart.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[sam4cm_cpustart.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[sam4cm_cpustart.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)

## Verification
- Run: `make test`
