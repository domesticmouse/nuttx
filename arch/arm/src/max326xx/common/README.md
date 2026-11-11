# common (`nuttx/arch/arm/src/max326xx/common`)

## Overview
Hardware abstraction and architecture package for `common` under `nuttx/arch/arm/src/max326xx/common`, providing 0 header file(s) and 8 source file(s) (including `max326_clrpend.c`, `max326_idle.c`, `max326_irq.c`, `max326_mpuinit.c`).

## Interface
- `[max326_clrpend.c:max326_clrpend]`
- `[max326_idle.c:up_idle]`
- `[max326_irq.c:up_irqinitialize]`
- `[max326_irq.c:up_disable_irq]`
- `[max326_irq.c:up_enable_irq]`
- `[max326_irq.c:arm_ack_irq]`
- `[max326_irq.c:up_prioritize_irq]`
- `[max326_mpuinit.c:max326_mpuinitialize]`
- `[max326_mpuinit.c:max326_mpu_uheap]`
- `[max326_rtc_lowerhalf.c:max326_rtc_lowerhalf]`
- `[max326_start.c:g_idle_topstack]`
- `[max326_start.c:__start]`
- `[max326_start.c:IDLE_STACK]`
- `[max326_timerisr.c:up_timer_initialize]`
- `[max326_userspace.c:max326_userspace]`
- `[CMakeLists.txt:target_sources]`

## Invariants
- `[max326_idle.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[max326_irq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[max326_irq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[max326_irq.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[max326_irq.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[max326_mpuinit.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[max326_rtc_lowerhalf.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[max326_rtc_lowerhalf.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[max326_timerisr.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[max326_userspace.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[max326_clrpend.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[max326_idle.c:nxsched_process_timer]` Advances the NuttX kernel system tick and scheduler timer state (`nxsched_process_timer`)
- `[max326_irq.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[max326_irq.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[max326_irq.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[max326_irq.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[max326_irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[max326_irq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[max326_start.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)
- `[max326_timerisr.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[max326_timerisr.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[max326_timerisr.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)

## Verification
- Run: `make test`
