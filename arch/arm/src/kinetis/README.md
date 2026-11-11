# kinetis (`nuttx/arch/arm/src/kinetis`)

## Overview
Hardware abstraction and architecture package for `kinetis` (Kinetis Configuration Options; Kinetis Peripheral Support) under `nuttx/arch/arm/src/kinetis`, providing 18 header file(s) and 34 source file(s) (including `chip.h`, `kinetis.h`, `kinetis_alarm.h`, `kinetis_config.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/kinetis/hardware`, providing 65 header file(s) and 0 source file(s) (including `kinetis_adc.h`, `kinetis_aips.h`, `kinetis_axbs.h`, `kinetis_cmp.h`).

## Interface
- `[chip.h:ARMV7M_PERIPHERAL_INTERRUPTS]`
- `[kinetis.h:kinetis_clockconfig]`
- `[kinetis.h:kinetis_earlyserialinit]`
- `[kinetis.h:kinetis_uart_earlyserialinit]`
- `[kinetis.h:kinetis_lpuart_earlyserialinit]`
- `[kinetis.h:kinetis_lowsetup]`
- `[kinetis.h:kinetis_uart_serialinit]`
- `[kinetis.h:kinetis_lpuart_serialinit]`
- `[kinetis.h:kinetis_uartreset]`
- `[kinetis.h:kinetis_lpuartreset]`
- `[kinetis.h:kinetis_uartconfigure]`
- `[kinetis.h:kinetis_lpuartconfigure]`
- `[kinetis.h:kinetis_wddisable]`
- `[kinetis.h:kinetis_pinconfig]`
- `[kinetis.h:kinetis_pinfilter]`
- `[kinetis.h:kinetis_gpiowrite]`
- `[kinetis.h:kinetis_gpioread]`
- `[kinetis.h:kinetis_pinirqinitialize]`
- `[kinetis.h:kinetis_pinirqattach]`
- `[kinetis.h:kinetis_pinirqenable]`
- `[kinetis.h:kinetis_pinirqdisable]`
- `[kinetis.h:kinetis_pindmaenable]`
- `[kinetis.h:kinetis_pindmadisable]`
- `[kinetis.h:kinetis_pindump]`
- `[kinetis.h:kinetis_clrpend]`
- `[kinetis.h:sdhc_initialize]`
- `[kinetis.h:sdhc_mediachange]`
- `[kinetis.h:sdhc_wrprotect]`
- `[kinetis.h:kinetis_netinitialize]`
- `[kinetis.h:kinetis_caninitialize]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[kinetis_pwm.h:#error]` Compile-time guard: CONFIG_KINETIS_FTM0_CHANNEL must be provided
- `[kinetis_tpm.h:#error]` Compile-time guard: No TMP definitions for this Kinetis part
- `[kinetis_allocateheap.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[kinetis_clockconfig.c:#error]` Compile-time configuration constraint: CONFIG_ARCH_RAMFUNCS must be defined for this logic
- `[kinetis_edma.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[kinetis_edma.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[kinetis_enet.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[kinetis_enet.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[kinetis_enet.c:#error]` Compile-time configuration constraint: Work queue support is required
- `[kinetis_flexcan.c:#error]` Compile-time configuration constraint: Work queue support is required
- `[kinetis_i2c.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[kinetis_i2c.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates

## Side Effects
- `[kinetis_clockconfig.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[kinetis_clockconfig.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[kinetis_clockconfig.c:putreg8]` Mutates 8-bit memory-mapped I/O (MMIO) hardware registers (`putreg8`)
- `[kinetis_clrpend.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[kinetis_dac.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[kinetis_dac.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[kinetis_dac.c:putreg8]` Mutates 8-bit memory-mapped I/O (MMIO) hardware registers (`putreg8`)
- `[kinetis_edma.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[kinetis_edma.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[kinetis_edma.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[kinetis_edma.c:putreg8]` Mutates 8-bit memory-mapped I/O (MMIO) hardware registers (`putreg8`)
- `[kinetis_edma.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)

## Verification
- Run: `make test`
