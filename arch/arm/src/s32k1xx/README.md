# s32k1xx (`nuttx/arch/arm/src/s32k1xx`)

## Overview
Hardware abstraction and architecture package for `s32k1xx` (S32K1XX Peripheral Selection; S32K1xx Reset Control Module (RCM)) under `nuttx/arch/arm/src/s32k1xx`, providing 22 header file(s) and 26 source file(s) (including `chip.h`, `s32k1xx_clockconfig.h`, `s32k1xx_config.h`, `s32k1xx_edma.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/s32k1xx/hardware`, providing 37 header file(s) and 0 source file(s) (including `s32k116_pinmux.h`, `s32k118_pinmux.h`, `s32k11x_dmamux.h`, `s32k142_pinmux.h`).
- `s32k11x`: [./s32k11x/README.md](./s32k11x/README.md) - Hardware abstraction and architecture package for `s32k11x` under `nuttx/arch/arm/src/s32k1xx/s32k11x`, providing 2 header file(s) and 4 source file(s) (including `s32k11x_clocknames.h`, `s32k11x_irq.h`, `s32k11x_clockmapping.c`, `s32k11x_irq.c`).
- `s32k14x`: [./s32k14x/README.md](./s32k14x/README.md) - Hardware abstraction and architecture package for `s32k14x` under `nuttx/arch/arm/src/s32k1xx/s32k14x`, providing 2 header file(s) and 5 source file(s) (including `s32k14x_clocknames.h`, `s32k14x_irq.h`, `s32k14x_clockmapping.c`, `s32k14x_clrpend.c`).

## Interface
- `[chip.h:ARMV6M_PERIPHERAL_INTERRUPTS]`
- `[chip.h:ARMV7M_PERIPHERAL_INTERRUPTS]`
- `[chip.h:ARMV7M_DCACHE_LINESIZE]`
- `[chip.h:ARMV7M_ICACHE_LINESIZE]`
- `[s32k1xx_clockconfig.h:s32k1xx_get_runmode]`
- `[s32k1xx_clockconfig.h:s32k1xx_set_runmode]`
- `[s32k1xx_clockconfig.h:s32k1xx_clockconfig]`
- `[s32k1xx_clockconfig.h:s32k1xx_clock_pm_register]`
- `[s32k1xx_clockconfig.h:s32k1xx_get_coreclk]`
- `[s32k1xx_clockconfig.h:s32k1xx_get_sysclk]`
- `[s32k1xx_clockconfig.h:s32k1xx_get_asnchfreq]`
- `[s32k1xx_clockconfig.h:scg_system_clock_type_e]`
- `[s32k1xx_clockconfig.h:scg_async_clock_type_e]`
- `[s32k1xx_clockconfig.h:scg_sirc_range_e]`
- `[s32k1xx_clockconfig.h:scg_async_clock_div_e]`
- `[s32k1xx_clockconfig.h:scg_sirc_config_s]`
- `[s32k1xx_clockconfig.h:scg_firc_range_e]`
- `[s32k1xx_clockconfig.h:scg_firc_config_s]`
- `[s32k1xx_clockconfig.h:scg_sosc_monitor_mode_e]`
- `[s32k1xx_clockconfig.h:scg_sosc_ext_ref_e]`
- `[s32k1xx_clockconfig.h:scg_sosc_gain_e]`
- `[s32k1xx_clockconfig.h:scg_sosc_range_e]`
- `[s32k1xx_clockconfig.h:scg_sosc_config_s]`
- `[s32k1xx_clockconfig.h:scg_spll_monitor_mode_e]`
- `[s32k1xx_clockconfig.h:scg_spll_config_s]`
- `[s32k1xx_clockconfig.h:scg_rtc_config_s]`
- `[s32k1xx_clockconfig.h:scg_clockout_src_e]`
- `[s32k1xx_clockconfig.h:scg_clockout_config_s]`
- `[s32k1xx_clockconfig.h:scg_system_clock_src_e]`
- `[s32k1xx_clockconfig.h:scg_system_clock_config_s]`
- [./hardware/README.md](./hardware/README.md)
- [./s32k11x/README.md](./s32k11x/README.md)
- [./s32k14x/README.md](./s32k14x/README.md)

## Invariants
- `[s32k1xx_progmem.h:#error]` Compile-time guard: Progmem size has to be a multiple of 2
- `[s32k1xx_pwm.h:#error]` Compile-time guard: CONFIG_S32K1XX_FTM0_CHANNEL must be provided
- `[s32k1xx_rtc.h:#error]` Compile-time guard: CONFIG_RTC_DATETIME should not be selected with this driver
- `[s32k1xx_serial.h:#error]` Compile-time guard: S32K1XX LPUART receive or transmit DMA requires CONFIG_S32K1XX_EDMA
- `[s32k1xx_clockconfig.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[s32k1xx_clockconfig.c:#error]` Compile-time configuration constraint: Make sure CMU is gated
- `[s32k1xx_edma.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[s32k1xx_edma.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[s32k1xx_eeeprom.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[s32k1xx_enet.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[s32k1xx_enet.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[s32k1xx_enet.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)

## Side Effects
- `[s32k1xx_wdog.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[s32k1xx_wdog.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[s32k1xx_clockconfig.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[s32k1xx_clockconfig.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[s32k1xx_clockconfig.c:putreg8]` Mutates 8-bit memory-mapped I/O (MMIO) hardware registers (`putreg8`)
- `[s32k1xx_edma.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[s32k1xx_edma.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[s32k1xx_edma.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[s32k1xx_edma.c:putreg8]` Mutates 8-bit memory-mapped I/O (MMIO) hardware registers (`putreg8`)
- `[s32k1xx_edma.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[s32k1xx_edma.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[s32k1xx_edma.c:up_clean_dcache]` Flushes CPU data cache lines to main memory (`up_clean_dcache`)

## Verification
- Run: `make test`
