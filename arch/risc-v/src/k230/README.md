# k230 (`nuttx/arch/risc-v/src/k230`)

## Overview
Hardware abstraction and architecture package for `k230` under `nuttx/arch/risc-v/src/k230`, providing 7 header file(s) and 11 source file(s) (including `chip.h`, `k230_hart.h`, `k230_ipi.h`, `k230_memorymap.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/risc-v/src/k230/hardware`, providing 3 header file(s) and 0 source file(s) (including `k230_clint.h`, `k230_memorymap.h`, `k230_plic.h`).

## Interface
- `[chip.h:k230_putc]`
- `[k230_hart.h:k230_hart_init]`
- `[k230_hart.h:k230_hart_is_big]`
- `[k230_hart.h:k230_hart_big_boot]`
- `[k230_hart.h:k230_hart_big_stop]`
- `[k230_hart.h:CSR_MSECCFG]`
- `[k230_hart.h:CSR_MSECCFGH]`
- `[k230_hart.h:MSECCFG_MML]`
- `[k230_hart.h:MSECCFG_RLB]`
- `[k230_ipi.h:k230_ipi_init]`
- `[k230_ipi.h:k230_ipi_notify]`
- `[k230_ipi.h:k230_ipi_finish]`
- `[k230_ipi.h:K230_IPI_DEVN_MAX]`
- `[k230_ipi.h:K230_IPI_LINE_MAX]`
- `[k230_ipi.h:K230_IPI_BASE]`
- `[k230_ipi.h:K230_IPI_M2R_INTEN]`
- `[k230_ipi.h:K230_IPI_M2R_INTSET]`
- `[k230_ipi.h:K230_IPI_M2R_INTCLR]`
- `[k230_ipi.h:K230_IPI_M2R_INTSTS]`
- `[k230_ipi.h:K230_IPI_M2R_INTERR]`
- `[k230_ipi.h:K230_IPI_R2M_INTEN]`
- `[k230_ipi.h:K230_IPI_R2M_INTSET]`
- `[k230_ipi.h:K230_IPI_R2M_INTCLR]`
- `[k230_ipi.h:K230_IPI_R2M_INTSTS]`
- `[k230_memorymap.h:K230_IDLESTACK_BASE]`
- `[k230_mm_init.h:k230_kernel_mappings]`
- `[k230_mm_init.h:k230_mm_init]`
- `[k230_rptun.h:k230_rptun_init]`
- `[k230_userspace.h:k230_userspace]`
- `[k230_allocateheap.c:up_allocate_kheap]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[k230_hart.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[k230_ipi.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[k230_irq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[k230_irq.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[k230_mm_init.c:#error]` Compile-time configuration constraint: No valid MMU type defined
- `[k230_pgalloc.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[k230_rptun.c:#error]` Compile-time configuration constraint: Invalid K230_RPTUN_IPI_DEV number
- `[k230_start.c:#error]` Compile-time configuration constraint: Target requires kernel in S-mode, enable CONFIG_ARCH_USE_S_MODE
- `[k230_timerisr.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[k230_userspace.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[k230_hart.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[k230_hart.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[k230_hart.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)
- `[k230_ipi.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[k230_ipi.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[k230_ipi.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[k230_ipi.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[k230_ipi.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[k230_irq.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[k230_irq.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[k230_irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[k230_irq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)

## Verification
- Run: `make test`
