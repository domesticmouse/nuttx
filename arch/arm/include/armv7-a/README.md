# armv7-a (`nuttx/arch/arm/include/armv7-a`)

## Overview
Hardware abstraction and architecture package for `armv7-a` under `nuttx/arch/arm/include/armv7-a`, providing 4 header file(s) and 0 source file(s) (including `barriers.h`, `cp14.h`, `cp15.h`, `irq.h`).

## Interface
- `[barriers.h:arm_dsb]`
- `[barriers.h:arm_dmb]`
- `[barriers.h:arm_isb]`
- `[barriers.h:arm_nop]`
- `[barriers.h:arm_yield]`
- `[barriers.h:UP_DSB]`
- `[barriers.h:UP_DMB]`
- `[barriers.h:UP_RMB]`
- `[barriers.h:UP_WMB]`
- `[barriers.h:UP_ISB]`
- `[barriers.h:UP_NOP]`
- `[barriers.h:UP_RELAX]`
- `[cp14.h:_CP14]`
- `[cp14.h:CP14_DBGDIDR]`
- `[cp14.h:CP14_DBGDSCRINT]`
- `[cp14.h:CP14_DBGDTRRXINT]`
- `[cp14.h:CP14_DBGDTRTXINT]`
- `[cp14.h:CP14_DBGWFAR]`
- `[cp14.h:CP14_DBGVCR]`
- `[cp14.h:CP14_DBGECR]`
- `[cp14.h:CP14_DBGDSCCR]`
- `[cp14.h:CP14_DBGDSMCR]`
- `[cp14.h:CP14_DBGDTRRXEXT]`
- `[cp15.h:_CP15]`
- `[cp15.h:_CP15_64]`
- `[cp15.h:CP15_MIDR]`
- `[cp15.h:CP15_CTR]`
- `[cp15.h:CP15_TCMTR]`
- `[cp15.h:CP15_TLBTR]`
- `[cp15.h:CP15_MPIDR]`

## Invariants
- None

## Side Effects
- `[barriers.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[cp14.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[cp15.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[irq.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations

## Verification
- Run: `make test`
