# xm6 (`nuttx/arch/ceva/include/xm6`)

## Overview
Hardware abstraction and architecture package for `xm6` under `nuttx/arch/ceva/include/xm6`, providing 4 header file(s) and 0 source file(s) (including `barriers.h`, `irq.h`, `math.h`, `reg.h`).

## Interface
- `[barriers.h:MSS_BARRIER]`
- `[irq.h:xcpt_syscall_s]`
- `[irq.h:xcptcontext]`
- `[irq.h:CONFIG_SYS_NNEST]`
- `[irq.h:REG_A0]`
- `[irq.h:REG_A1]`
- `[irq.h:REG_A2]`
- `[irq.h:REG_A3]`
- `[irq.h:REG_A4]`
- `[irq.h:REG_A5]`
- `[irq.h:REG_A6]`
- `[irq.h:REG_FP]`
- `[irq.h:REG_LR]`
- `[irq.h:REG_PC]`
- `[irq.h:REG_OM]`
- `[math.h:roundf]`
- `[math.h:round]`
- `[math.h:roundl]`
- `[math.h:gamma]`
- `[math.h:lgamma]`
- `[math.h:log2f]`
- `[math.h:log2]`
- `[math.h:log2l]`
- `[reg.h:REG_SP]`
- `[reg.h:REG_MODI]`
- `[reg.h:REG_MODG]`
- `[reg.h:REG_MODE]`
- `[reg.h:REG_MODD]`
- `[reg.h:REG_MODC]`
- `[reg.h:REG_MODA]`

## Invariants
- None

## Side Effects
- `[barriers.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[irq.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations

## Verification
- Run: `make test`
