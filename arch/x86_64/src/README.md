# src (`nuttx/arch/x86_64/src`)

## Overview
Architectural grouping for `nuttx/arch/x86_64/src`, coordinating 2 component subdirectories (`common`, `intel64`).

## Subdirectories & Boundaries
- `common`: [./common/README.md](./common/README.md) - Hardware abstraction and architecture package for `common` (Common Configuration Options) under `nuttx/arch/x86_64/src/common`, providing 6 header file(s) and 29 source file(s) (including `addrenv.h`, `pgalloc.h`, `x86_64_fork.h`, `x86_64_hwdebug.h`).
- `intel64`: [./intel64/README.md](./intel64/README.md) - Hardware abstraction and architecture package for `intel64` (intel64 Configuration Options) under `nuttx/arch/x86_64/src/intel64`, providing 6 header file(s) and 41 source file(s) (including `chip.h`, `intel64.h`, `intel64_cpu.h`, `intel64_hpet.h`).

## Interface
- `[Makefile:CHIP_CSRCS]`
- `[Makefile:CMN_CSRCS]`
- `[Makefile:CSRCS]`
- `[Makefile:ASRCS]`
- [./common/README.md](./common/README.md)
- [./intel64/README.md](./intel64/README.md)

## Invariants
- `[x86_64_acpi.c:#error]` Compile-time configuration constraint: For now only ACPI from BIOS region is supported
- `[x86_64_acpi_procfs.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[x86_64_addrenv.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[x86_64_addrenv.c:#error]` Compile-time configuration constraint: CONFIG_RAM_VSTART != 0x100000000
- `[x86_64_addrenv_kstack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[x86_64_allocateheap.c:#error]` Compile-time configuration constraint: CONFIG_IDLETHREAD_STACKSIZE must be aligned to 16

## Side Effects
- `[x86_64_internal.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[x86_64_internal.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[x86_64_internal.h:modifyreg32]` Performs atomic read-modify-write updates on 32-bit MMIO registers
- `[x86_64_internal.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[crt0.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)
- `[x86_64_exit.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)

## Verification
- Run: `make test`
