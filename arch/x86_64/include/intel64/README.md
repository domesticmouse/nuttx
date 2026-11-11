# intel64 (`nuttx/arch/x86_64/include/intel64`)

## Overview
Hardware abstraction and architecture package for `intel64` under `nuttx/arch/x86_64/include/intel64`, providing 6 header file(s) and 0 source file(s) (including `arch.h`, `inttypes.h`, `io.h`, `irq.h`).

## Interface
- `[arch.h:up_map_region]`
- `[arch.h:x86_64_check_and_enable_capability]`
- `[arch.h:x86_64_syscall_entry]`
- `[arch.h:idt_entry_s]`
- `[arch.h:idt_ptr_s]`
- `[arch.h:gdt_entry_s]`
- `[arch.h:gdt_ptr_s]`
- `[arch.h:ist_s]`
- `[arch.h:tss_s]`
- `[arch.h:X86_64_LOAD_OFFSET]`
- `[arch.h:X86_64_PGPOOL_SIZE]`
- `[arch.h:X86_64_PGPOOL_BASE]`
- `[arch.h:X86_64_RFLAGS_CF]`
- `[arch.h:X86_64_RFLAGS_PF]`
- `[arch.h:X86_64_RFLAGS_AF]`
- `[arch.h:X86_64_RFLAGS_ZF]`
- `[arch.h:X86_64_RFLAGS_SF]`
- `[arch.h:X86_64_RFLAGS_TF]`
- `[arch.h:X86_64_RFLAGS_IF]`
- `[arch.h:X86_64_RFLAGS_DF]`
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

## Invariants
- `[arch.h:#error]` Compile-time guard: CONFIG_ARCH_X86_64_PGPOOL_SIZE must be multiple of page size

## Side Effects
- `[io.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[irq.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations

## Verification
- Run: `make test`
