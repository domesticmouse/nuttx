# lm32 (`nuttx/arch/misoc/src/lm32`)

## Overview
Hardware abstraction and architecture package for `lm32` under `nuttx/arch/misoc/src/lm32`, providing 3 header file(s) and 19 source file(s) (including `chip.h`, `lm32.h`, `lm32_config.h`, `lm32_allocateheap.c`).

## Interface
- `[lm32.h:lm32_board_initialize]`
- `[lm32.h:lm32_copystate]`
- `[lm32.h:lm32_decodeirq]`
- `[lm32.h:lm32_doirq]`
- `[lm32.h:lm32_swint]`
- `[lm32.h:lm32_sigdeliver]`
- `[lm32.h:lm32_flush_dcache]`
- `[lm32.h:lm32_flush_icache]`
- `[lm32.h:misoc_savestate]`
- `[lm32.h:up_copystate]`
- `[lm32.h:misoc_restorestate]`
- `[lm32.h:USE_SERIALDRIVER]`
- `[lm32.h:USE_EARLYSERIALINIT]`
- `[lm32_config.h:HAVE_UART_DEVICE]`
- `[lm32_config.h:HAVE_SERIAL_CONSOLE]`
- `[lm32_allocateheap.c:up_allocate_heap]`
- `[lm32_copystate.c:lm32_copystate]`
- `[lm32_createstack.c:up_create_stack]`
- `[lm32_decodeirq.c:lm32_decodeirq]`
- `[lm32_doirq.c:lm32_doirq]`
- `[lm32_exit.c:up_exit]`
- `[lm32_flushcache.c:lm32_flush_dcache]`
- `[lm32_flushcache.c:lm32_flush_icache]`
- `[lm32_idle.c:up_idle]`
- `[lm32_initialstate.c:up_initial_state]`
- `[lm32_irq.c:up_irqinitialize]`
- `[lm32_irq.c:up_irq_save]`
- `[lm32_irq.c:up_irq_restore]`
- `[lm32_irq.c:up_irq_enable]`
- `[lm32_irq.c:up_disable_irq]`

## Invariants
- `[lm32_createstack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[lm32_doirq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[lm32_irq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[lm32_irq.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[lm32_sigdeliver.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[lm32_sigdeliver.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[lm32_swint.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[lm32_swint.c:#error]` Compile-time configuration constraint: Missing logic
- `[lm32_usestack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[chip.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[lm32_doirq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[lm32_doirq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[lm32_idle.c:nxsched_process_timer]` Advances the NuttX kernel system tick and scheduler timer state (`nxsched_process_timer`)
- `[lm32_irq.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[lm32_irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[lm32_irq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[lm32_swint.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)

## Verification
- Run: `make test`
