# include (`nuttx/arch/misoc/include`)

## Overview
Hardware abstraction and architecture package for `include` under `nuttx/arch/misoc/include`, providing 7 header file(s) and 0 source file(s) (including `arch.h`, `inttypes.h`, `irq.h`, `limits.h`).

## Subdirectories & Boundaries
- `lm32`: [./lm32/README.md](./lm32/README.md) - Hardware abstraction and architecture package for `lm32` under `nuttx/arch/misoc/include/lm32`, providing 1 header file(s) and 0 source file(s) (including `irq.h`).
- `minerva`: [./minerva/README.md](./minerva/README.md) - Hardware abstraction and architecture package for `minerva` under `nuttx/arch/misoc/include/minerva`, providing 2 header file(s) and 0 source file(s) (including `csrdefs.h`, `irq.h`).

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
- `[irq.h:up_irq_save]`
- `[irq.h:up_irq_enable]`
- `[irq.h:up_irq_restore]`
- `[irq.h:up_interrupt_context]`
- `[limits.h:CHAR_BIT]`
- `[limits.h:SCHAR_MIN]`
- `[limits.h:SCHAR_MAX]`
- `[limits.h:UCHAR_MAX]`
- `[limits.h:CHAR_MIN]`
- `[limits.h:CHAR_MAX]`
- `[limits.h:SHRT_MIN]`
- `[limits.h:SHRT_MAX]`
- `[limits.h:USHRT_MAX]`
- `[limits.h:INT_MIN]`
- `[stdarg.h:va_list]`
- `[stdarg.h:va_start]`
- `[stdarg.h:va_end]`
- `[stdarg.h:va_arg]`
- [./lm32/README.md](./lm32/README.md)
- [./minerva/README.md](./minerva/README.md)

## Invariants
- None

## Side Effects
- `[irq.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations

## Verification
- Run: `make test`
