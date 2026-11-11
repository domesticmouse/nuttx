# include (`nuttx/arch/hc/include`)

## Overview
Hardware abstraction and architecture package for `include` under `nuttx/arch/hc/include`, providing 6 header file(s) and 0 source file(s) (including `arch.h`, `inttypes.h`, `irq.h`, `limits.h`).

## Subdirectories & Boundaries
- `hc12`: [./hc12/README.md](./hc12/README.md) - Hardware abstraction and architecture package for `hc12` under `nuttx/arch/hc/include/hc12`, providing 3 header file(s) and 0 source file(s) (including `irq.h`, `limits.h`, `types.h`).
- `hcs12`: [./hcs12/README.md](./hcs12/README.md) - Hardware abstraction and architecture package for `hcs12` under `nuttx/arch/hc/include/hcs12`, providing 3 header file(s) and 0 source file(s) (including `irq.h`, `limits.h`, `types.h`).
- `m9s12`: [./m9s12/README.md](./m9s12/README.md) - Hardware abstraction and architecture package for `m9s12` under `nuttx/arch/hc/include/m9s12`, providing 1 header file(s) and 0 source file(s) (including `irq.h`).

## Interface
- `[inttypes.h:PRId8]`
- `[inttypes.h:PRId16]`
- `[inttypes.h:PRId32]`
- `[inttypes.h:PRId64]`
- `[inttypes.h:PRIdPTR]`
- `[inttypes.h:PRIi8]`
- `[inttypes.h:PRIi16]`
- `[inttypes.h:PRIi32]`
- `[inttypes.h:PRIi64]`
- `[inttypes.h:PRIiPTR]`
- `[inttypes.h:PRIo8]`
- `[inttypes.h:PRIo16]`
- `[irq.h:STACKFRAME_ALIGN]`
- `[irq.h:up_interrupt_context]`
- [./hc12/README.md](./hc12/README.md)
- [./hcs12/README.md](./hcs12/README.md)
- [./m9s12/README.md](./m9s12/README.md)

## Invariants
- None

## Side Effects
- `[irq.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations

## Verification
- Run: `make test`
