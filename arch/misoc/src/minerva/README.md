# minerva (`nuttx/arch/misoc/src/minerva`)

## Overview
Hardware abstraction and architecture package for `minerva` under `nuttx/arch/misoc/src/minerva`, providing 3 header file(s) and 20 source file(s) (including `chip.h`, `minerva.h`, `minerva_config.h`, `minerva_allocateheap.c`).

## Interface
- `[chip.h:CSR_IRQ_MASK]`
- `[chip.h:CSR_IRQ_PENDING]`
- `[chip.h:CSR_DCACHE_INFO]`
- `[chip.h:csrr]`
- `[chip.h:csrw]`
- `[chip.h:csrs]`
- `[chip.h:csrc]`
- `[minerva.h:minerva_board_initialize]`
- `[minerva.h:minerva_copystate]`
- `[minerva.h:minerva_decodeirq]`
- `[minerva.h:minerva_doirq]`
- `[minerva.h:minerva_swint]`
- `[minerva.h:minerva_sigdeliver]`
- `[minerva.h:minerva_flush_dcache]`
- `[minerva.h:minerva_flush_icache]`
- `[minerva.h:misoc_savestate]`
- `[minerva.h:up_copystate]`
- `[minerva.h:misoc_restorestate]`
- `[minerva.h:USE_SERIALDRIVER]`
- `[minerva.h:USE_EARLYSERIALINIT]`
- `[minerva_config.h:HAVE_UART_DEVICE]`
- `[minerva_config.h:HAVE_SERIAL_CONSOLE]`
- `[minerva_allocateheap.c:up_allocate_heap]`
- `[minerva_copystate.c:minerva_copystate]`
- `[minerva_createstack.c:up_create_stack]`
- `[minerva_decodeirq.c:minerva_decodeirq]`
- `[minerva_doexceptions.c:minerva_doexception]`
- `[minerva_doirq.c:minerva_doirq]`
- `[minerva_exit.c:up_exit]`
- `[minerva_flushcache.c:minerva_flush_dcache]`

## Invariants
- `[minerva_createstack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[minerva_doirq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[minerva_irq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[minerva_irq.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[minerva_sigdeliver.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[minerva_sigdeliver.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[minerva_swint.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[minerva_swint.c:#error]` Compile-time configuration constraint: Missing logic
- `[minerva_usestack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[minerva_doirq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[minerva_doirq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[minerva_idle.c:nxsched_process_timer]` Advances the NuttX kernel system tick and scheduler timer state (`nxsched_process_timer`)
- `[minerva_irq.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[minerva_irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[minerva_irq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)

## Verification
- Run: `make test`
