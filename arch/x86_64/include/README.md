# include (`nuttx/arch/x86_64/include`)

## Overview
Hardware abstraction and architecture package for `include` under `nuttx/arch/x86_64/include`, providing 13 header file(s) and 0 source file(s) (including `acpi.h`, `arch.h`, `barriers.h`, `elf.h`).

## Subdirectories & Boundaries
- `intel64`: [./intel64/README.md](./intel64/README.md) - Hardware abstraction and architecture package for `intel64` under `nuttx/arch/x86_64/include/intel64`, providing 6 header file(s) and 0 source file(s) (including `arch.h`, `inttypes.h`, `io.h`, `irq.h`).
- `qemu`: [./qemu/README.md](./qemu/README.md) - Hardware abstraction and architecture package for `qemu` under `nuttx/arch/x86_64/include/qemu`, providing 2 header file(s) and 0 source file(s) (including `arch.h`, `irq.h`).

## Interface
- `[acpi.h:acpi_init]`
- `[acpi.h:acpi_madt_get]`
- `[acpi.h:acpi_lapic_get]`
- `[acpi.h:acpi_poweroff_param_get]`
- `[acpi.h:acpi_dump]`
- `[acpi.h:acpi_table_get]`
- `[acpi.h:acpi_procfs_register]`
- `[acpi.h:acpi_rsdp_s]`
- `[acpi.h:acpi_sdt_s]`
- `[acpi.h:acpi_rsdt_s]`
- `[acpi.h:acpi_xsdt_s]`
- `[acpi.h:acpi_facp_s]`
- `[acpi.h:acpi_entry_s]`
- `[acpi.h:acpi_madt_s]`
- `[acpi.h:acpi_lapic_s]`
- `[acpi.h:acpi_pciseg_s]`
- `[acpi.h:acpi_mcfg_s]`
- `[acpi.h:ACPI_SIG_RSDP]`
- `[acpi.h:ACPI_SIG_APIC]`
- `[acpi.h:ACPI_SIG_BERT]`
- `[acpi.h:ACPI_SIG_BGRT]`
- `[acpi.h:ACPI_SIG_CCEL]`
- `[acpi.h:ACPI_SIG_CPEP]`
- `[acpi.h:ACPI_SIG_DSDT]`
- `[acpi.h:ACPI_SIG_ECDT]`
- `[acpi.h:ACPI_SIG_EINJ]`
- `[acpi.h:ACPI_SIG_ERST]`
- `[acpi.h:ACPI_SIG_FACP]`
- `[acpi.h:ACPI_SIG_FACS]`
- `[arch.h:arch_addrenv_s]`
- [./intel64/README.md](./intel64/README.md)
- [./qemu/README.md](./qemu/README.md)

## Invariants
- None

## Side Effects
- `[barriers.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[irq.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[syscall.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations

## Verification
- Run: `make test`
