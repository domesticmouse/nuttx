# xc5 (`nuttx/arch/ceva/include/xc5`)

## Overview
Hardware abstraction and architecture package for `xc5` under `nuttx/arch/ceva/include/xc5`, providing 4 header file(s) and 0 source file(s) (including `barriers.h`, `irq.h`, `math.h`, `reg.h`).

## Interface
- `[irq.h:xcpt_syscall_s]`
- `[irq.h:xcptcontext]`
- `[irq.h:CONFIG_SYS_NNEST]`
- `[irq.h:REG_FP]`
- `[irq.h:REG_LR]`
- `[irq.h:REG_PC]`
- `[irq.h:REG_OM]`
- `[irq.h:REG_MODG_DEFAULT]`
- `[irq.h:REG_MODP_DEFAULT]`
- `[irq.h:REG_MODP_ENABLE]`
- `[irq.h:REG_MODP_DISABLE]`
- `[irq.h:REG_MODPB_DEFAULT]`
- `[irq.h:REG_OM_DEFAULT]`
- `[irq.h:REG_OM_KERNEL]`
- `[math.h:roundf]`
- `[math.h:round]`
- `[math.h:roundl]`
- `[math.h:gamma]`
- `[math.h:lgamma]`
- `[math.h:log2f]`
- `[math.h:log2]`
- `[math.h:log2l]`
- `[reg.h:REG_SP]`
- `[reg.h:REG_BKNEST40]`
- `[reg.h:REG_BKNEST41]`
- `[reg.h:REG_BKNEST30]`
- `[reg.h:REG_BKNEST31]`
- `[reg.h:REG_BKNEST20]`
- `[reg.h:REG_BKNEST21]`
- `[reg.h:REG_MODU2D]`

## Invariants
- None

## Side Effects
- `[irq.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations

## Verification
- Run: `make test`
