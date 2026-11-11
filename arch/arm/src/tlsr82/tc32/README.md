# tc32 (`nuttx/arch/arm/src/tlsr82/tc32`)

## Overview
Hardware abstraction and architecture package for `tc32` under `nuttx/arch/arm/src/tlsr82/tc32`, providing 1 header file(s) and 6 source file(s) (including `tc32.h`, `tc32_backtrace.c`, `tc32_doirq.c`, `tc32_initialstate.c`).

## Interface
- `[tc32.h:PSR_MODE_MASK]`
- `[tc32.h:PSR_MODE_IRQ]`
- `[tc32.h:PSR_MODE_SVC]`
- `[tc32.h:PSR_I_BIT]`
- `[tc32.h:PSR_J_BIT]`
- `[tc32.h:PSR_Q_BIT]`
- `[tc32.h:PSR_V_BIT]`
- `[tc32.h:PSR_C_BIT]`
- `[tc32.h:PSR_Z_BIT]`
- `[tc32.h:PSR_N_BIT]`
- `[tc32_backtrace.c:up_backtrace_init_code_regions]`
- `[tc32_backtrace.c:up_backtrace]`
- `[tc32_doirq.c:arm_doirq]`
- `[tc32_initialstate.c:up_initial_state]`
- `[tc32_schedulesigaction.c:up_schedule_sigaction]`
- `[tc32_syscall.c:arm_syscall]`
- `[Make.defs:CHIP_CSRCS]`
- `[Make.defs:CMN_CSRCS]`
- `[Make.defs:HEAD_ASRC]`

## Invariants
- `[tc32_doirq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[tc32_doirq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[tc32_syscall.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation

## Side Effects
- `[tc32_backtrace.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)

## Verification
- Run: `make test`
