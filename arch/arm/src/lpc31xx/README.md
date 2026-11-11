# lpc31xx (`nuttx/arch/arm/src/lpc31xx`)

## Overview
Hardware abstraction and architecture package for `lpc31xx` (LPC31xx Configuration Options; LPC31xx Peripheral Support) under `nuttx/arch/arm/src/lpc31xx`, providing 28 header file(s) and 26 source file(s) (including `chip.h`, `lpc31.h`, `lpc31_adc.h`, `lpc31_analogdie.h`).

## Interface
- `[chip.h:LPC31_NDMACH]`
- `[chip.h:HAVE_INTSRAM1]`
- `[chip.h:HAVE_AESENGINE]`
- `[chip.h:ARM_DCACHE_LINESIZE]`
- `[chip.h:ARM_ICACHE_LINESIZE]`
- `[lpc31.h:lpc31_lowsetup]`
- `[lpc31.h:lpc31_clockconfig]`
- `[lpc31.h:lpc31_spibus_initialize]`
- `[lpc31.h:lpc31_spiselect]`
- `[lpc31.h:lpc31_spistatus]`
- `[lpc31.h:lpc31_spicmddata]`
- `[lpc31.h:lpc31_usbpullup]`
- `[lpc31.h:lpc31_usbsuspend]`
- `[lpc31.h:lpc31_ehci_initialize]`
- `[lpc31.h:lpc31_usbhost_vbusdrive]`
- `[lpc31.h:sdio_initialize]`
- `[lpc31.h:sdio_mediachange]`
- `[lpc31.h:sdio_wrprotect]`
- `[lpc31_adc.h:LPC31_ADC_VBASE]`
- `[lpc31_adc.h:LPC31_ADC_PBASE]`
- `[lpc31_adc.h:LPC31_ADC_R0_OFFSET]`
- `[lpc31_adc.h:LPC31_ADC_R1_OFFSET]`
- `[lpc31_adc.h:LPC31_ADC_R2_OFFSET]`
- `[lpc31_adc.h:LPC31_ADC_R3_OFFSET]`
- `[lpc31_adc.h:LPC31_ADC_CON_OFFSET]`
- `[lpc31_adc.h:LPC31_ADC_CSEL_OFFSET]`
- `[lpc31_adc.h:LPC31_ADC_INTEN_OFFSET]`
- `[lpc31_adc.h:LPC31_ADC_INTST_OFFSET]`
- `[lpc31_adc.h:LPC31_ADC_INTCLR_OFFSET]`
- `[lpc31_adc.h:LPC31_ADC_R0]`

## Invariants
- `[chip.h:#error]` Compile-time guard: Unsupported LPC31XX architecture
- `[lpc31_memorymap.h:#error]` Compile-time guard: Only one of PGTABLE_BASE_PADDR or PGTABLE_BASE_VADDR is defined
- `[lpc31_allocateheap.c:#error]` Compile-time configuration constraint: CONFIG_MM_REGIONS is not large enough for the selected memory regions
- `[lpc31_decodeirq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[lpc31_decodeirq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[lpc31_ehci.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[lpc31_ehci.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[lpc31_ehci.c:#error]` Compile-time configuration constraint: Work queue support is required (CONFIG_SCHED_WORKQUEUE)
- `[lpc31_i2c.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[lpc31_i2c.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[lpc31_serial.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[lpc31_spi.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[lpc31.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[lpc31.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[lpc31_cgudrvr.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[lpc31_cgudrvr.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[lpc31_boot.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[lpc31_clkexten.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[lpc31_clkexten.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[lpc31_clkfreq.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[lpc31_clkinit.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[lpc31_clkinit.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[lpc31_decodeirq.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[lpc31_defclk.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)

## Verification
- Run: `make test`
