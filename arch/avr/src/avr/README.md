# avr (`nuttx/arch/avr/src/avr`)

## Overview
Hardware abstraction and architecture package for `avr` (AVR Configuration Options) under `nuttx/arch/avr/src/avr`, providing 2 header file(s) and 14 source file(s) (including `avr.h`, `excptmacros.h`, `avr_checkstack.c`, `avr_copystate.c`).

## Interface
- `[avr.h:avr_copystate]`
- `[avr.h:avr_switchcontext]`
- `[avr.h:avr_doirq]`
- `[avr.h:avr_spibus_initialize]`
- `[avr.h:avr_spiselect]`
- `[avr.h:avr_spistatus]`
- `[avr.h:avr_spicmddata]`
- `[avr.h:avr_savestate]`
- `[avr.h:avr_restorestate]`
- `[avr_checkstack.c:avr_color_intstack]`
- `[avr_checkstack.c:avr_stack_check]`
- `[avr_checkstack.c:up_check_tcbstack]`
- `[avr_checkstack.c:up_check_intstack]`
- `[avr_copystate.c:avr_copystate]`
- `[avr_createstack.c:up_create_stack]`
- `[avr_doirq.c:avr_doirq]`
- `[avr_initialstate.c:up_initial_state]`
- `[avr_irq.c:up_irqinitialize]`
- `[avr_registerdump.c:up_dump_register]`
- `[avr_romgetc.c:up_romgetc]`
- `[avr_schedulesigaction.c:up_schedule_sigaction]`
- `[avr_sigdeliver.c:avr_sigdeliver]`
- `[avr_spi.c:avr_spibus_initialize]`
- `[avr_stackframe.c:up_stack_frame]`
- `[avr_switchcontext.c:up_switch_context]`
- `[avr_usestack.c:up_use_stack]`
- `[Kconfig:CONFIG_AVR_WINAVR_TOOLCHAIN]`
- `[Kconfig:CONFIG_AVR_ATMEL_AVR_TOOLCHAIN]`
- `[Kconfig:CONFIG_AVR_LINUXGCC_TOOLCHAIN]`
- `[Kconfig:CONFIG_AVR_CROSSPACK_TOOLCHAIN]`

## Invariants
- `[avr_createstack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[avr_doirq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[avr_sigdeliver.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[avr_sigdeliver.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[avr_spi.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[avr_spi.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[avr_usestack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- None

## Verification
- Run: `make test`
