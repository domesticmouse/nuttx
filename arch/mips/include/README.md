# include (`nuttx/arch/mips/include`)

## Overview
Hardware abstraction and architecture package for `include` under `nuttx/arch/mips/include`, providing 7 header file(s) and 0 source file(s) (including `arch.h`, `elf.h`, `inttypes.h`, `irq.h`).

## Subdirectories & Boundaries
- `jz4780`: [./jz4780/README.md](./jz4780/README.md) - Hardware abstraction and architecture package for `jz4780` under `nuttx/arch/mips/include/jz4780`, providing 4 header file(s) and 0 source file(s) (including `chip.h`, `cp0.h`, `irq.h`, `irq_jz4780.h`).
- `mips32`: [./mips32/README.md](./mips32/README.md) - Hardware abstraction and architecture package for `mips32` under `nuttx/arch/mips/include/mips32`, providing 3 header file(s) and 0 source file(s) (including `cp0.h`, `irq.h`, `registers.h`).
- `pic32mx`: [./pic32mx/README.md](./pic32mx/README.md) - Hardware abstraction and architecture package for `pic32mx` under `nuttx/arch/mips/include/pic32mx`, providing 6 header file(s) and 0 source file(s) (including `chip.h`, `cp0.h`, `irq.h`, `irq_1xx2xx.h`).
- `pic32mz`: [./pic32mz/README.md](./pic32mz/README.md) - Hardware abstraction and architecture package for `pic32mz` under `nuttx/arch/mips/include/pic32mz`, providing 6 header file(s) and 0 source file(s) (including `chip.h`, `cp0.h`, `irq.h`, `irq_pic32mzw1.h`).

## Interface
- `[elf.h:arch_elfdata_s]`
- `[elf.h:hi_rel_s]`
- `[elf.h:arch_elfdata_t]`
- `[elf.h:R_MIPS_NONE]`
- `[elf.h:R_MIPS_32]`
- `[elf.h:R_MIPS_26]`
- `[elf.h:R_MIPS_HI16]`
- `[elf.h:R_MIPS_LO16]`
- `[elf.h:MIPS_HI16_COUNT]`
- `[elf.h:ARCH_ELFDATA]`
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
- `[irq.h:up_getusrpc]`
- `[irq.h:up_getusrsp]`
- `[limits.h:CHAR_BIT]`
- `[limits.h:SCHAR_MIN]`
- `[limits.h:SCHAR_MAX]`
- `[limits.h:UCHAR_MAX]`
- [./jz4780/README.md](./jz4780/README.md)
- [./mips32/README.md](./mips32/README.md)
- [./pic32mx/README.md](./pic32mx/README.md)
- [./pic32mz/README.md](./pic32mz/README.md)

## Invariants
- None

## Side Effects
- `[irq.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[syscall.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations

## Verification
- Run: `make test`
