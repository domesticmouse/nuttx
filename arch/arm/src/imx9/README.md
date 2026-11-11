# imx9 (`nuttx/arch/arm/src/imx9`)

## Overview
Hardware abstraction and architecture package for `imx9` (i.MX9 Peripheral Selection; FLEXCAN Peripherals) under `nuttx/arch/arm/src/imx9`, providing 21 header file(s) and 27 source file(s) (including `chip.h`, `imx9_ccm.h`, `imx9_clockconfig.h`, `imx9_edma.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/imx9/hardware`, providing 23 header file(s) and 0 source file(s) (including `imx9_ccm.h`, `imx9_clock.h`, `imx9_dmamux.h`, `imx9_edma.h`).

## Interface
- `[chip.h:ARMV7M_DCACHE_LINESIZE]`
- `[chip.h:ARMV7M_ICACHE_LINESIZE]`
- `[imx9_ccm.h:imx9_ccm_configure_root_clock]`
- `[imx9_ccm.h:imx9_ccm_root_clock_on]`
- `[imx9_ccm.h:imx9_ccm_gate_on]`
- `[imx9_clockconfig.h:imx9_clockconfig]`
- `[imx9_clockconfig.h:imx9_configure_clock]`
- `[imx9_clockconfig.h:imx9_get_rootclock]`
- `[imx9_edma.h:imx9_dmach_alloc]`
- `[imx9_edma.h:imx9_dmach_free]`
- `[imx9_edma.h:imx9_dmach_xfrsetup]`
- `[imx9_edma.h:imx9_dmach_start]`
- `[imx9_edma.h:imx9_dmach_stop]`
- `[imx9_edma.h:imx9_dmach_getcount]`
- `[imx9_edma.h:imx9_dmach_idle]`
- `[imx9_edma.h:imx9_dmasample]`
- `[imx9_edma.h:imx9_dmadump]`
- `[imx9_edma.h:imx9_edma_xfrtype_e]`
- `[imx9_edma.h:imx9_edma_sizes_e]`
- `[imx9_edma.h:imx9_edma_xfrconfig_s]`
- `[imx9_edma.h:imx9_dmaregs_s]`
- `[imx9_edma.h:DMACH_HANDLE]`
- `[imx9_edma.h:EDMA_CONFIG_LINKTYPE_SHIFT]`
- `[imx9_edma.h:EDMA_CONFIG_LINKTYPE_MASK]`
- `[imx9_edma.h:EDMA_CONFIG_LINKTYPE_LINKNONE]`
- `[imx9_edma.h:EDMA_CONFIG_LINKTYPE_MINORLINK]`
- `[imx9_edma.h:EDMA_CONFIG_LINKTYPE_MAJORLINK]`
- `[imx9_edma.h:EDMA_CONFIG_LOOP_SHIFT]`
- `[imx9_edma.h:EDMA_CONFIG_LOOP_MASK]`
- `[imx9_edma.h:EDMA_CONFIG_LOOPNONE]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[imx9_serial.h:#error]` Compile-time guard: IMXRT LPUART receive or transmit DMA requires CONFIG_IMX9_EDMA
- `[imx9_allocateheap.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[imx9_edma.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[imx9_edma.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[imx9_flexcan.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[imx9_flexcan.c:#error]` Compile-time configuration constraint: Work queue support is required
- `[imx9_flexio.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[imx9_flexspi.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[imx9_gpio.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[imx9_gpio.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[imx9_gpiobase.c:#error]` Compile-time configuration constraint: Unrecognized i.MX9 architecture
- `[imx9_gpioirq.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates

## Side Effects
- `[imx9_ccm.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[imx9_ccm.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[imx9_clockconfig.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[imx9_clockconfig.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[imx9_edma.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[imx9_edma.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[imx9_edma.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[imx9_edma.c:putreg8]` Mutates 8-bit memory-mapped I/O (MMIO) hardware registers (`putreg8`)
- `[imx9_edma.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[imx9_edma.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[imx9_edma.c:up_clean_dcache]` Flushes CPU data cache lines to main memory (`up_clean_dcache`)
- `[imx9_flexcan.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)

## Verification
- Run: `make test`
