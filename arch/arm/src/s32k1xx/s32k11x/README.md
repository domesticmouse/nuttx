# s32k11x (`nuttx/arch/arm/src/s32k1xx/s32k11x`)

## Overview
Hardware abstraction and architecture package for `s32k11x` under `nuttx/arch/arm/src/s32k1xx/s32k11x`, providing 2 header file(s) and 4 source file(s) (including `s32k11x_clocknames.h`, `s32k11x_irq.h`, `s32k11x_clockmapping.c`, `s32k11x_irq.c`).

## Interface
- `[s32k11x_clocknames.h:clock_names_e]`
- `[s32k11x_irq.h:s32k11x_dumpnvic]`
- `[s32k11x_clockmapping.c:g_clkname_mapping]`
- `[s32k11x_irq.c:up_irqinitialize]`
- `[s32k11x_irq.c:up_disable_irq]`
- `[s32k11x_irq.c:up_enable_irq]`
- `[s32k11x_irq.c:arm_ack_irq]`
- `[s32k11x_irq.c:s32k11x_dumpnvic]`
- `[s32k11x_periphfeatures.c:g_periph_features]`
- `[s32k11x_timerisr.c:up_timer_initialize]`
- `[CMakeLists.txt:target_sources]`
- `[Make.defs:CHIP_CSRCS]`

## Invariants
- `[s32k11x_irq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[s32k11x_irq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[s32k11x_irq.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[s32k11x_irq.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[s32k11x_timerisr.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[s32k11x_irq.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[s32k11x_irq.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[s32k11x_irq.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[s32k11x_irq.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[s32k11x_irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[s32k11x_irq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[s32k11x_timerisr.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[s32k11x_timerisr.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[s32k11x_timerisr.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[s32k11x_timerisr.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[s32k11x_timerisr.c:nxsched_process_timer]` Advances the NuttX kernel system tick and scheduler timer state (`nxsched_process_timer`)

## Verification
- Run: `make test`
