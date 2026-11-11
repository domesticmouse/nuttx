# s32k3xx (`nuttx/arch/arm/src/s32k3xx`)

## Overview
Hardware abstraction and architecture package for `s32k3xx` (S32K3XX Heap Configuration; S32K3XX Peripheral Selection) under `nuttx/arch/arm/src/s32k3xx`, providing 21 header file(s) and 25 source file(s) (including `chip.h`, `s32k3xx_clockconfig.h`, `s32k3xx_clocknames.h`, `s32k3xx_config.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/s32k3xx/hardware`, providing 46 header file(s) and 0 source file(s) (including `s32k344_pinmux.h`, `s32k3xx_adc.h`, `s32k3xx_axbs.h`, `s32k3xx_dcm.h`).

## Interface
- `[chip.h:ARMV6M_PERIPHERAL_INTERRUPTS]`
- `[chip.h:ARMV7M_PERIPHERAL_INTERRUPTS]`
- `[chip.h:ARMV7M_DCACHE_LINESIZE]`
- `[chip.h:ARMV7M_ICACHE_LINESIZE]`
- `[s32k3xx_clockconfig.h:s32k3xx_clockconfig]`
- `[s32k3xx_clockconfig.h:s32k3xx_get_coreclk]`
- `[s32k3xx_clockconfig.h:s32k3xx_get_sysclk]`
- `[s32k3xx_clockconfig.h:s32k3xx_get_freq]`
- `[s32k3xx_clockconfig.h:cgm_system_clock_type_e]`
- `[s32k3xx_clockconfig.h:cgm_csc_src_e]`
- `[s32k3xx_clockconfig.h:cgm_sirc_range_e]`
- `[s32k3xx_clockconfig.h:cgm_sirc_config_s]`
- `[s32k3xx_clockconfig.h:cgm_firc_range_e]`
- `[s32k3xx_clockconfig.h:cgm_firc_clock_div_e]`
- `[s32k3xx_clockconfig.h:cgm_firc_config_s]`
- `[s32k3xx_clockconfig.h:cgm_mux_div_e]`
- `[s32k3xx_clockconfig.h:cgm_mux_div_slow_e]`
- `[s32k3xx_clockconfig.h:cgm_scs_source_e]`
- `[s32k3xx_clockconfig.h:cgm_mux_config_s]`
- `[s32k3xx_clockconfig.h:cgm_mux_slow_config_s]`
- `[s32k3xx_clockconfig.h:cgm_mux_src_config_s]`
- `[s32k3xx_clockconfig.h:cgm_scs_config_s]`
- `[s32k3xx_clockconfig.h:scg_spll_monitor_mode_e]`
- `[s32k3xx_clockconfig.h:cgm_pll_core_mode_e]`
- `[s32k3xx_clockconfig.h:cgm_pll_sigma_delta_e]`
- `[s32k3xx_clockconfig.h:cgm_pll_postdiv_e]`
- `[s32k3xx_clockconfig.h:cgm_pll_phi_div_e]`
- `[s32k3xx_clockconfig.h:cgm_pll_config_s]`
- `[s32k3xx_clockconfig.h:cgm_clkout_div_e]`
- `[s32k3xx_clockconfig.h:cgm_clkout_config_s]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[s32k3xx_serial.h:#error]` Compile-time guard: IMXRT LPUART receive or transmit DMA requires CONFIG_S32K3XX_EDMA
- `[s32k3xx_allocateheap.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[s32k3xx_edma.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[s32k3xx_edma.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[s32k3xx_emac.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[s32k3xx_emac.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[s32k3xx_emac.c:#error]` Compile-time configuration constraint: Work queue support is required
- `[s32k3xx_flexcan.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[s32k3xx_flexcan.c:#error]` Compile-time configuration constraint: Work queue support is required
- `[s32k3xx_fs26.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[s32k3xx_fs26.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[s32k3xx_irq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[s32k3xx_swt.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[s32k3xx_clockconfig.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[s32k3xx_clockconfig.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[s32k3xx_clrpend.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[s32k3xx_edma.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[s32k3xx_edma.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[s32k3xx_edma.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[s32k3xx_edma.c:putreg8]` Mutates 8-bit memory-mapped I/O (MMIO) hardware registers (`putreg8`)
- `[s32k3xx_edma.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[s32k3xx_edma.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[s32k3xx_edma.c:up_clean_dcache]` Flushes CPU data cache lines to main memory (`up_clean_dcache`)
- `[s32k3xx_emac.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)

## Verification
- Run: `make test`
