# i486 (`nuttx/arch/x86/include/i486`)

## Overview
Hardware abstraction and architecture package for `i486` under `nuttx/arch/x86/include/i486`, providing 6 header file(s) and 0 source file(s) (including `arch.h`, `inttypes.h`, `io.h`, `irq.h`).

## Interface
- `[arch.h:gdt_flush]`
- `[arch.h:idt_flush]`
- `[arch.h:gdt_entry_s]`
- `[arch.h:gdt_ptr_s]`
- `[arch.h:idt_entry_s]`
- `[arch.h:idt_ptr_s]`
- `[arch.h:X86_FLAGS_CF]`
- `[arch.h:X86_FLAGS_PF]`
- `[arch.h:X86_FLAGS_AF]`
- `[arch.h:X86_FLAGS_ZF]`
- `[arch.h:X86_FLAGS_SF]`
- `[arch.h:X86_FLAGS_TF]`
- `[arch.h:X86_FLAGS_IF]`
- `[arch.h:X86_FLAGS_DF]`
- `[arch.h:X86_FLAGS_OF]`
- `[arch.h:X86_FLAGS_IOPL_SHIFT]`
- `[arch.h:X86_FLAGS_IOPL_MASK]`
- `[arch.h:X86_FLAGS_NT]`
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

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
