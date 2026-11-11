# avr32 (`nuttx/arch/avr/src/avr32`)

## Overview
Hardware abstraction and architecture package for `avr32` (AVR32 Configuration Options) under `nuttx/arch/avr/src/avr32`, providing 1 header file(s) and 10 source file(s) (including `avr32.h`, `avr_copystate.c`, `avr_createstack.c`, `avr_doirq.c`).

## Interface
- `[avr32.h:avr_copystate]`
- `[avr32.h:avr_switchcontext]`
- `[avr32.h:avr_doirq]`
- `[avr32.h:avr_savestate]`
- `[avr32.h:avr_restorestate]`
- `[avr_copystate.c:avr_copystate]`
- `[avr_createstack.c:up_create_stack]`
- `[avr_doirq.c:avr_doirq]`
- `[avr_initialstate.c:up_initial_state]`
- `[avr_registerdump.c:up_dump_register]`
- `[avr_schedulesigaction.c:up_schedule_sigaction]`
- `[avr_sigdeliver.c:avr_sigdeliver]`
- `[avr_stackframe.c:up_stack_frame]`
- `[avr_switchcontext.c:up_switch_context]`
- `[avr_usestack.c:up_use_stack]`
- `[Kconfig:CONFIG_AVR32_AVRTOOLSW]`
- `[Kconfig:CONFIG_AVR32_AVRTOOLSL]`

## Invariants
- `[avr_createstack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[avr_doirq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[avr_doirq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[avr_initialstate.c:#error]` Compile-time configuration constraint: Missing logic for the CONFIG_BUILD_KERNEL build
- `[avr_sigdeliver.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[avr_sigdeliver.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[avr_usestack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- None

## Verification
- Run: `make test`
