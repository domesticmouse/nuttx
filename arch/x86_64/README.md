# x86_64 (`nuttx/arch/x86_64`)

## Overview
Architectural grouping for `nuttx/arch/x86_64` (x86_64 Configuration Options), coordinating 2 component subdirectories (`include`, `src`).

## Subdirectories & Boundaries
- `include`: [./include/README.md](./include/README.md) - Hardware abstraction and architecture package for `include` under `nuttx/arch/x86_64/include`, providing 13 header file(s) and 0 source file(s) (including `acpi.h`, `arch.h`, `barriers.h`, `elf.h`).
- `src`: [./src/README.md](./src/README.md) - Architectural grouping for `nuttx/arch/x86_64/src`, coordinating 2 component subdirectories (`common`, `intel64`).

## Interface
- `[Kconfig:CONFIG_ARCH_INTEL64]`
- `[Kconfig:CONFIG_ARCH_CHIP_INTEL64_QEMU]`
- `[Kconfig:CONFIG_ARCH_CHIP_INTEL64]`
- `[Kconfig:CONFIG_ARCH_CHIP_X86_64_CUSTOM]`
- `[Kconfig:CONFIG_ARCH_CHIP]`
- `[Kconfig:CONFIG_X86_64_UNWINDER_FRAME_POINTER]`
- `[Kconfig:CONFIG_ARCH_HAVE_MMX]`
- `[Kconfig:CONFIG_ARCH_HAVE_SSE]`
- [./include/README.md](./include/README.md)
- [./src/README.md](./src/README.md)

## Invariants
- `[x86_64_acpi.c:#error]` Compile-time configuration constraint: For now only ACPI from BIOS region is supported
- `[x86_64_acpi_procfs.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[x86_64_addrenv.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[x86_64_addrenv.c:#error]` Compile-time configuration constraint: CONFIG_RAM_VSTART != 0x100000000
- `[x86_64_addrenv_kstack.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[x86_64_allocateheap.c:#error]` Compile-time configuration constraint: CONFIG_IDLETHREAD_STACKSIZE must be aligned to 16

## Side Effects
- `[barriers.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[irq.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[syscall.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[x86_64_internal.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[x86_64_internal.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[x86_64_internal.h:modifyreg32]` Performs atomic read-modify-write updates on 32-bit MMIO registers

## Verification
- Run: `make test`
