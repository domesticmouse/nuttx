# mips32 (`nuttx/arch/mips/include/mips32`)

## Overview
Hardware abstraction and architecture package for `mips32` under `nuttx/arch/mips/include/mips32`, providing 3 header file(s) and 0 source file(s) (including `cp0.h`, `irq.h`, `registers.h`).

## Interface
- `[cp0.h:MIPS32_CP0_INDEX1]`
- `[cp0.h:MIPS32_CP0_RANDOM1]`
- `[cp0.h:MIPS32_CP0_ENTRYLO01]`
- `[cp0.h:MIPS32_CP0_ENTRYLO11]`
- `[cp0.h:MIPS32_CP0_CONTEXT2]`
- `[cp0.h:MIPS32_CP0_PAGEMASK1]`
- `[cp0.h:MIPS32_CP0_WIRED1]`
- `[cp0.h:MIPS32_CP0_BADVADDR]`
- `[cp0.h:MIPS32_CP0_COUNT]`
- `[cp0.h:MIPS32_CP0_ENTRYHI1]`
- `[cp0.h:MIPS32_CP0_COMPARE]`
- `[cp0.h:MIPS32_CP0_STATUS]`
- `[irq.h:up_irq_save]`
- `[irq.h:up_irq_restore]`
- `[irq.h:up_irq_enable]`
- `[irq.h:xcpt_syscall_s]`
- `[irq.h:xcptcontext]`
- `[irq.h:MIPS32_SAVE_GP]`
- `[irq.h:CONFIG_SYS_NNEST]`
- `[irq.h:REG_MFLO_NDX]`
- `[irq.h:REG_MFHI_NDX]`
- `[irq.h:REG_EPC_NDX]`
- `[irq.h:REG_STATUS_NDX]`
- `[irq.h:REG_R1_NDX]`
- `[irq.h:REG_R2_NDX]`
- `[irq.h:REG_R3_NDX]`
- `[irq.h:REG_R4_NDX]`
- `[irq.h:REG_R5_NDX]`
- `[irq.h:REG_R6_NDX]`
- `[registers.h:zero]`

## Invariants
- None

## Side Effects
- `[irq.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations

## Verification
- Run: `make test`
