# i486 (`nuttx/arch/x86/src/i486`)

## Overview
Hardware abstraction and architecture package for `i486` (i486 Configuration Options) under `nuttx/arch/x86/src/i486`, providing 0 header file(s) and 10 source file(s) (including `i486_createstack.c`, `i486_initialstate.c`, `i486_irq.c`, `i486_regdump.c`).

## Interface
- `[i486_createstack.c:up_create_stack]`
- `[i486_initialstate.c:up_initial_state]`
- `[i486_irq.c:up_irqinitialize]`
- `[i486_irq.c:up_disable_irq]`
- `[i486_irq.c:up_enable_irq]`
- `[i486_irq.c:up_prioritize_irq]`
- `[i486_regdump.c:up_dump_register]`
- `[i486_releasestack.c:up_release_stack]`
- `[i486_savestate.c:x86_savestate]`
- `[i486_schedulesigaction.c:up_schedule_sigaction]`
- `[i486_sigdeliver.c:x86_sigdeliver]`
- `[i486_stackframe.c:up_stack_frame]`
- `[i486_usestack.c:up_use_stack]`

## Invariants
- `[i486_createstack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[i486_initialstate.c:#error]` Compile-time configuration constraint: Missing logic for the CONFIG_BUILD_KERNEL build
- `[i486_savestate.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[i486_sigdeliver.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[i486_sigdeliver.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[i486_usestack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[i486_irq.c:outb]` Writes bytes to CPU I/O ports (`outb`)
- `[i486_irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[i486_irq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)

## Verification
- Run: `make test`
