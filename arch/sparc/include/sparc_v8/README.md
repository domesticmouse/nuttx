# sparc_v8 (`nuttx/arch/sparc/include/sparc_v8`)

## Overview
Hardware abstraction and architecture package for `sparc_v8` under `nuttx/arch/sparc/include/sparc_v8`, providing 1 header file(s) and 0 source file(s) (including `irq.h`).

## Interface
- `[irq.h:up_irq_save]`
- `[irq.h:up_irq_restore]`
- `[irq.h:up_irq_enable]`
- `[irq.h:up_irq_disable]`
- `[irq.h:xcpt_syscall_s]`
- `[irq.h:xcptcontext]`
- `[irq.h:SPARC_V8_SAVE_GP]`
- `[irq.h:CONFIG_SYS_NNEST]`
- `[irq.h:REG_R1]`
- `[irq.h:REG_R2]`
- `[irq.h:REG_R3]`
- `[irq.h:REG_R4]`
- `[irq.h:REG_R5]`
- `[irq.h:REG_R6]`
- `[irq.h:REG_R7]`
- `[irq.h:REG_R8]`
- `[irq.h:REG_R9]`
- `[irq.h:REG_R10]`

## Invariants
- None

## Side Effects
- `[irq.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations

## Verification
- Run: `make test`
