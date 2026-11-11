# rm57 (`nuttx/arch/arm/src/rm57`)

## Overview
Hardware abstraction and architecture package for `rm57` (RM57 Configuration Options; RM57 Peripheral Support) under `nuttx/arch/arm/src/rm57`, providing 18 header file(s) and 25 source file(s) (including `chip.h`, `rm57_adc.h`, `rm57_boot.h`, `rm57_clockconfig.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/rm57/hardware`, providing 23 header file(s) and 0 source file(s) (including `rm57_adc.h`, `rm57_ccm.h`, `rm57_dcan.h`, `rm57_dma.h`).

## Interface
- `[chip.h:ARMV7A_DCACHE_LINESIZE]`
- `[chip.h:ARMV7A_ICACHE_LINESIZE]`
- `[rm57_adc.h:rm57_adc_initialize]`
- `[rm57_adc.h:rm57_adc_calibrate]`
- `[rm57_adc.h:rm57_adc_midpointcal]`
- `[rm57_adc.h:rm57_adc_selftest]`
- `[rm57_adc.h:rm57_adc_readtemp]`
- `[rm57_adc.h:rm57_adc_tempcal_points]`
- `[rm57_adc.h:rm57_adc_temp_register]`
- `[rm57_boot.h:rm57_boot_c]`
- `[rm57_boot.h:rm57_board_initialize]`
- `[rm57_clockconfig.h:rm57_clockconfig]`
- `[rm57_dcan.h:rm57can_instance]`
- `[rm57_dcan.h:rm57can_init]`
- `[rm57_dcan.h:rm57can_setup]`
- `[rm57_dcan.h:rm57can_shutdown]`
- `[rm57_dcan.h:rm57can_timing_from_baud]`
- `[rm57_dcan.h:rm57can_set_timing]`
- `[rm57_dcan.h:rm57can_send]`
- `[rm57_dcan.h:rm57can_txready]`
- `[rm57_dcan.h:rm57can_txempty]`
- `[rm57_dcan.h:rm57can_add_filter]`
- `[rm57_dcan.h:rm57can_del_filter]`
- `[rm57_dcan.h:rm57can_connmodes]`
- `[rm57_dcan.h:rm57can_set_nart]`
- `[rm57_dcan.h:rm57can_set_abom]`
- `[rm57_dcan.h:rm57can_busoff_recovery]`
- `[rm57_dcan.h:rm57can_rxint]`
- `[rm57_dcan.h:rm57can_txint]`
- `[rm57_dcan.h:rm57_dcan_chardev_initialize]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[rm57_adc.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[rm57_adc.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[rm57_adc.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[rm57_adc.c:static_assert]` Enforces compile-time size and alignment invariants via `static_assert`
- `[rm57_boot.c:#error]` Compile-time configuration constraint: CONFIG_ARMV7R_MEMINIT is required by this architecture.
- `[rm57_dcan.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[rm57_dcan.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[rm57_dcan.c:#error]` Compile-time configuration constraint: RM57_DCAN_RXFIFO_DEPTH exceeds the available RX mailboxes
- `[rm57_dma.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[rm57_dma.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[rm57_esm.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[rm57_ethernet.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[rm57_adc.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[rm57_adc.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[rm57_adc.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[rm57_adc.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[rm57_adc.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[rm57_adc.c:up_invalidate_dcache]` Invalidates CPU data cache lines prior to DMA/memory reads (`up_invalidate_dcache`)
- `[rm57_boot.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[rm57_boot.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[rm57_clockconfig.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[rm57_clockconfig.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[rm57_dcan.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[rm57_dcan.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)

## Verification
- Run: `make test`
