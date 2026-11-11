# include (`nuttx/arch/ceva/include`)

## Overview
Hardware abstraction and architecture package for `include` under `nuttx/arch/ceva/include`, providing 9 header file(s) and 0 source file(s) (including `arch.h`, `barriers.h`, `inttypes.h`, `irq.h`).

## Subdirectories & Boundaries
- `xc5`: [./xc5/README.md](./xc5/README.md) - Hardware abstraction and architecture package for `xc5` under `nuttx/arch/ceva/include/xc5`, providing 4 header file(s) and 0 source file(s) (including `barriers.h`, `irq.h`, `math.h`, `reg.h`).
- `xm6`: [./xm6/README.md](./xm6/README.md) - Hardware abstraction and architecture package for `xm6` under `nuttx/arch/ceva/include/xm6`, providing 4 header file(s) and 0 source file(s) (including `barriers.h`, `irq.h`, `math.h`, `reg.h`).

## Interface
- `[arch.h:CONFIG_ARCH_INTERRUPTSTACK]`
- `[arch.h:UMM_HEAP]`
- `[arch.h:KMM_HEAP]`
- `[arch.h:MM_HEAP]`
- `[barriers.h:UP_DSB]`
- `[barriers.h:UP_DMB]`
- `[barriers.h:UP_RMB]`
- `[barriers.h:UP_WMB]`
- `[inttypes.h:PRId8]`
- `[inttypes.h:PRId16]`
- `[inttypes.h:PRId32]`
- `[inttypes.h:PRId64]`
- `[inttypes.h:PRIdLEAST8]`
- `[inttypes.h:PRIdLEAST16]`
- `[inttypes.h:PRIdLEAST32]`
- `[inttypes.h:PRIdLEAST64]`
- `[inttypes.h:PRIdFAST8]`
- `[inttypes.h:PRIdFAST16]`
- `[inttypes.h:PRIdFAST32]`
- `[inttypes.h:PRIdFAST64]`
- `[irq.h:IRQ_VINT0]`
- `[irq.h:IRQ_VINT1]`
- `[irq.h:IRQ_VINT2]`
- `[irq.h:IRQ_VINT3]`
- `[irq.h:IRQ_VINT4]`
- `[irq.h:IRQ_VINT5]`
- `[irq.h:IRQ_VINT6]`
- `[irq.h:IRQ_VINT7]`
- `[irq.h:IRQ_VINT8]`
- `[irq.h:IRQ_VINT9]`
- [./xc5/README.md](./xc5/README.md)
- [./xm6/README.md](./xm6/README.md)

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
