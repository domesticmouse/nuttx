# include (`nuttx/arch/sparc/include`)

## Overview
Hardware abstraction and architecture package for `include` under `nuttx/arch/sparc/include`, providing 7 header file(s) and 0 source file(s) (including `arch.h`, `elf.h`, `inttypes.h`, `irq.h`).

## Subdirectories & Boundaries
- `bm3803`: [./bm3803/README.md](./bm3803/README.md) - Hardware abstraction and architecture package for `bm3803` under `nuttx/arch/sparc/include/bm3803`, providing 1 header file(s) and 0 source file(s) (including `irq.h`).
- `bm3823`: [./bm3823/README.md](./bm3823/README.md) - Hardware abstraction and architecture package for `bm3823` under `nuttx/arch/sparc/include/bm3823`, providing 1 header file(s) and 0 source file(s) (including `irq.h`).
- `s698pm`: [./s698pm/README.md](./s698pm/README.md) - Hardware abstraction and architecture package for `s698pm` under `nuttx/arch/sparc/include/s698pm`, providing 1 header file(s) and 0 source file(s) (including `irq.h`).
- `sparc_v8`: [./sparc_v8/README.md](./sparc_v8/README.md) - Hardware abstraction and architecture package for `sparc_v8` under `nuttx/arch/sparc/include/sparc_v8`, providing 1 header file(s) and 0 source file(s) (including `irq.h`).

## Interface
- `[elf.h:R_SPARC_NONE]`
- `[elf.h:R_SPARC_8]`
- `[elf.h:R_SPARC_16]`
- `[elf.h:R_SPARC_32]`
- `[elf.h:R_SPARC_DISP8]`
- `[elf.h:R_SPARC_DISP16]`
- `[elf.h:R_SPARC_DISP32]`
- `[elf.h:R_SPARC_WDISP30]`
- `[elf.h:R_SPARC_WDISP22]`
- `[elf.h:R_SPARC_HI22]`
- `[elf.h:R_SPARC_22]`
- `[elf.h:R_SPARC_13]`
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
- `[irq.h:up_getusrpc]`
- `[irq.h:up_getusrsp]`
- `[limits.h:CHAR_BIT]`
- `[limits.h:SCHAR_MIN]`
- `[limits.h:SCHAR_MAX]`
- [./bm3803/README.md](./bm3803/README.md)
- [./bm3823/README.md](./bm3823/README.md)
- [./s698pm/README.md](./s698pm/README.md)
- [./sparc_v8/README.md](./sparc_v8/README.md)

## Invariants
- None

## Side Effects
- `[irq.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations

## Verification
- Run: `make test`
