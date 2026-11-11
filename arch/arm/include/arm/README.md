# arm (`nuttx/arch/arm/include/arm`)

## Overview
Hardware abstraction and architecture package for `arm` under `nuttx/arch/arm/include/arm`, providing 2 header file(s) and 0 source file(s) (including `barriers.h`, `irq.h`).

## Interface
- `[barriers.h:arm_mb]`
- `[barriers.h:UP_DSB]`
- `[barriers.h:UP_ISB]`
- `[barriers.h:UP_DMB]`
- `[barriers.h:UP_RMB]`
- `[barriers.h:UP_WMB]`
- `[irq.h:xcptcontext]`
- `[irq.h:REG_R0]`
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
- `[irq.h:REG_R11]`

## Invariants
- None

## Side Effects
- `[barriers.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[irq.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations

## Verification
- Run: `make test`
