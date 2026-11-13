# arm_a_r (`nuttx/arch/arm/src/arm_a_r`)

## Overview
Shared ARMv7-A, ARMv7-R, and ARMv8-R signal scheduling and signal delivery trampoline implementation (`CONFIG_ENABLE_ALL_SIGNALS`) under `nuttx/arch/arm/src/arm_a_r`, providing 2 source file(s) (`arm_schedulesigaction.c`, `arm_sigdeliver.c`).

## Interface
- `[arm_schedulesigaction.c:up_schedule_sigaction]` Schedules asynchronous signal delivery on `tcb` by duplicating `tcb->xcp.regs` (`XCPTCONTEXT_SIZE`) onto the stack and redirecting `REG_PC` to `arm_sigdeliver` with `PSR_MODE_SYS | PSR_I_BIT | PSR_F_BIT`.
- `[arm_sigdeliver.c:arm_sigdeliver]` Signal handling trampoline that enables interrupts, invokes `rtcb->sigdeliver(rtcb)`, restores critical section state, and restores the saved register context via `arm_fullcontextrestore()`.

## Invariants
- `[arm_schedulesigaction.c:up_schedule_sigaction]` Must be called from within a critical section.
- `[arm_sigdeliver.c:DEBUGASSERT]` Asserts `rtcb->sigdeliver != NULL` and (under `CONFIG_SMP`) `saved_irqcount >= 0` and `rtcb->irqcount == 0` before restoring critical section locks.
- `[arm_sigdeliver.c:enter_critical_section]` Drops and re-acquires SMP critical section locks (`leave_critical_section` / `enter_critical_section`) around user/kernel signal delivery.

## Side Effects
- `[arm_schedulesigaction.c:up_schedule_sigaction]` Modifies `tcb->xcp.saved_regs` and `tcb->xcp.regs` (`REG_SP`, `REG_LR`, `REG_PC`, `REG_CPSR`).
- `[arm_sigdeliver.c:arm_sigdeliver]` Toggles `LED_SIGNAL` via `board_autoled_on` / `board_autoled_off`, enables/disables local interrupts (`up_irq_enable` / `up_irq_save`), invokes `rtcb->sigdeliver`, and restores CPU context via `arm_fullcontextrestore()`.

## Verification
- Run: `make test`
