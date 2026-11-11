# armv6-m (`nuttx/arch/arm/include/armv6-m`)

## Overview
Hardware abstraction and architecture package for `armv6-m` under `nuttx/arch/arm/include/armv6-m`, providing 2 header file(s) and 0 source file(s) (including `barriers.h`, `irq.h`).

## Interface
- `[barriers.h:arm_dsb]`
- `[barriers.h:arm_isb]`
- `[barriers.h:arm_dmb]`
- `[barriers.h:arm_rmb]`
- `[barriers.h:arm_wmb]`
- `[barriers.h:UP_DSB]`
- `[barriers.h:UP_ISB]`
- `[barriers.h:UP_DMB]`
- `[barriers.h:UP_RMB]`
- `[barriers.h:UP_WMB]`
- `[irq.h:xcpt_syscall_s]`
- `[irq.h:xcptcontext]`
- `[irq.h:__ARM_ARCH]`
- `[irq.h:CONFIG_SYS_NNEST]`
- `[irq.h:REG_R13]`
- `[irq.h:REG_PRIMASK]`
- `[irq.h:REG_R4]`
- `[irq.h:REG_R5]`
- `[irq.h:REG_R6]`
- `[irq.h:REG_R7]`
- `[irq.h:REG_R8]`
- `[irq.h:REG_R9]`
- `[irq.h:REG_R10]`
- `[irq.h:REG_R11]`

## Invariants
- None

## Side Effects
- `[barriers.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[irq.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations

## Verification
- Run: `make test`
