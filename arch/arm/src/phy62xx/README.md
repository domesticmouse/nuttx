# phy62xx (`nuttx/arch/arm/src/phy62xx`)

## Overview
Hardware abstraction and architecture package for `phy62xx` (PHY62xx Configuration Options) under `nuttx/arch/arm/src/phy62xx`, providing 27 header file(s) and 22 source file(s) (including `bus_dev.h`, `chip.h`, `clock.h`, `core_bumbee_m0.h`).

## Subdirectories & Boundaries
- `ble`: [./ble/README.md](./ble/README.md) - Hardware abstraction and architecture package for `ble` under `nuttx/arch/arm/src/phy62xx/ble`, providing 1 header file(s) and 0 source file(s) (including `ble_controller.h`).

## Interface
- `[bus_dev.h:IRQn_Type]`
- `[bus_dev.h:PHY_MCU_TYPE]`
- `[bus_dev.h:M0_IRQ_BASE]`
- `[bus_dev.h:__I]`
- `[bus_dev.h:__O]`
- `[bus_dev.h:__IO]`
- `[bus_dev.h:__IM]`
- `[bus_dev.h:__OM]`
- `[bus_dev.h:__IOM]`
- `[bus_dev.h:NVIC_DisableIRQ]`
- `[bus_dev.h:NVIC_EnableIRQ]`
- `[chip.h:ARMV6M_PERIPHERAL_INTERRUPTS]`
- `[clock.h:clk_get_pclk]`
- `[clock.h:hal_clk_gate_enable]`
- `[clock.h:hal_clk_gate_disable]`
- `[clock.h:hal_clk_gate_get]`
- `[clock.h:hal_clk_get_modules_state]`
- `[clock.h:hal_clk_reset]`
- `[clock.h:hal_clk_rf_config]`
- `[clock.h:hal_clk_rxadc_config]`
- `[clock.h:hal_clk_set_pclk]`
- `[clock.h:hal_clk_init]`
- `[clock.h:hal_rtc_clock_config]`
- `[clock.h:hal_systick]`
- `[clock.h:hal_ms_intv]`
- `[clock.h:rtc_get_counter]`
- `[clock.h:WaitMs]`
- `[clock.h:WaitUs]`
- `[clock.h:hal_system_soft_reset]`
- `[clock.h:clk_init]`
- [./ble/README.md](./ble/README.md)

## Invariants
- `[log.h:#error]` Compile-time guard: DEBUG_INFO undefined!
- `[irq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[irq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[irq.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[phy62xx_hardfault.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[phy62xx_hardfault.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[phyplus_gpio.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[phyplus_stub.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[phyplus_tim.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[phyplus_timer_lowerhalf.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[phyplus_timer_lowerhalf.c:ASSERT]` Enforces unconditional runtime assertions via `ASSERT`
- `[phyplus_wdt.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[idle.c:nxsched_process_timer]` Advances the NuttX kernel system tick and scheduler timer state (`nxsched_process_timer`)
- `[irq.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[irq.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[irq.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[irq.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[irq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[phyplus_tim.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[phyplus_tim.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[phyplus_tim.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[phyplus_tim.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[phyplus_tim.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)

## Verification
- Run: `make test`
