# armv8-r (`nuttx/arch/arm/include/armv8-r`)

## Overview
Hardware abstraction and architecture package for `armv8-r` under `nuttx/arch/arm/include/armv8-r`, providing 3 header file(s) and 0 source file(s) (including `barriers.h`, `cp15.h`, `irq.h`).

## Interface
- `[barriers.h:arm_dsb]`
- `[barriers.h:arm_dmb]`
- `[barriers.h:arm_rmb]`
- `[barriers.h:arm_wmb]`
- `[barriers.h:arm_isb]`
- `[barriers.h:arm_nop]`
- `[barriers.h:UP_DSB]`
- `[barriers.h:UP_DMB]`
- `[barriers.h:UP_RMB]`
- `[barriers.h:UP_WMB]`
- `[barriers.h:UP_ISB]`
- `[barriers.h:UP_NOP]`
- `[cp15.h:_CP15]`
- `[cp15.h:_CP15_64]`
- `[cp15.h:CP15_MIDR]`
- `[cp15.h:CP15_CTR]`
- `[cp15.h:CP15_TCMTR]`
- `[cp15.h:CP15_MPUIR]`
- `[cp15.h:CP15_HMPUIR]`
- `[cp15.h:CP15_MPIDR]`
- `[cp15.h:CP15_REVIDR]`
- `[cp15.h:CP15_MID_PFR0]`
- `[irq.h:xcpt_syscall_s]`
- `[irq.h:xcptcontext]`
- `[irq.h:__ARM_ARCH]`
- `[irq.h:REG_D0]`
- `[irq.h:REG_S0]`
- `[irq.h:REG_S1]`
- `[irq.h:REG_D1]`
- `[irq.h:REG_S2]`

## Invariants
- None

## Side Effects
- `[barriers.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[cp15.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[irq.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations

## Verification
- Run: `make test`
