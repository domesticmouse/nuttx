# include (`nuttx/arch/z80/include`)

## Overview
Hardware abstraction and architecture package for `include` under `nuttx/arch/z80/include`, providing 7 header file(s) and 0 source file(s) (including `arch.h`, `inttypes.h`, `io.h`, `irq.h`).

## Subdirectories & Boundaries
- `ez80`: [./ez80/README.md](./ez80/README.md) - Hardware abstraction and architecture package for `ez80` under `nuttx/arch/z80/include/ez80`, providing 6 header file(s) and 0 source file(s) (including `arch.h`, `inttypes.h`, `io.h`, `irq.h`).
- `z180`: [./z180/README.md](./z180/README.md) - Hardware abstraction and architecture package for `z180` under `nuttx/arch/z80/include/z180`, providing 7 header file(s) and 0 source file(s) (including `arch.h`, `chip.h`, `inttypes.h`, `io.h`).
- `z8`: [./z8/README.md](./z8/README.md) - Hardware abstraction and architecture package for `z8` under `nuttx/arch/z80/include/z8`, providing 5 header file(s) and 0 source file(s) (including `arch.h`, `inttypes.h`, `irq.h`, `limits.h`).
- `z80`: [./z80/README.md](./z80/README.md) - Hardware abstraction and architecture package for `z80` under `nuttx/arch/z80/include/z80`, providing 7 header file(s) and 0 source file(s) (including `arch.h`, `chip.h`, `inttypes.h`, `io.h`).

## Interface
- `[irq.h:up_getsp]`
- `[irq.h:STACKFRAME_ALIGN]`
- `[irq.h:up_getusrpc]`
- `[irq.h:up_getusrsp]`
- [./ez80/README.md](./ez80/README.md)
- [./z180/README.md](./z180/README.md)
- [./z8/README.md](./z8/README.md)
- [./z80/README.md](./z80/README.md)

## Invariants
- None

## Side Effects
- `[irq.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations

## Verification
- Run: `make test`
