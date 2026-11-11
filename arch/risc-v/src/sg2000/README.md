# sg2000 (`nuttx/arch/risc-v/src/sg2000`)

## Overview
Hardware abstraction and architecture package for `sg2000` under `nuttx/arch/risc-v/src/sg2000`, providing 3 header file(s) and 7 source file(s) (including `chip.h`, `sg2000_memorymap.h`, `sg2000_mm_init.h`, `sg2000_allocateheap.c`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/risc-v/src/sg2000/hardware`, providing 2 header file(s) and 0 source file(s) (including `sg2000_memorymap.h`, `sg2000_plic.h`).

## Interface
- `[sg2000_memorymap.h:SG2000_IDLESTACK_BASE]`
- `[sg2000_mm_init.h:sg2000_kernel_mappings]`
- `[sg2000_mm_init.h:sg2000_mm_init]`
- `[sg2000_allocateheap.c:up_allocate_kheap]`
- `[sg2000_irq.c:up_irqinitialize]`
- `[sg2000_irq.c:up_disable_irq]`
- `[sg2000_irq.c:up_enable_irq]`
- `[sg2000_irq.c:up_irq_enable]`
- `[sg2000_irq_dispatch.c:riscv_dispatch_irq]`
- `[sg2000_mm_init.c:sg2000_kernel_mappings]`
- `[sg2000_mm_init.c:sg2000_mm_init]`
- `[sg2000_mm_init.c:mmu_flush_cache]`
- `[sg2000_pgalloc.c:up_allocate_pgheap]`
- `[sg2000_start.c:sg2000_clear_bss]`
- `[sg2000_start.c:sg2000_start_s]`
- `[sg2000_start.c:sg2000_start]`
- `[sg2000_start.c:riscv_earlyserialinit]`
- `[sg2000_start.c:riscv_serialinit]`
- `[sg2000_timerisr.c:up_timer_initialize]`
- `[Make.defs:CHIP_CSRCS]`
- `[Make.defs:HEAD_ASRC]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[sg2000_irq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[sg2000_irq.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[sg2000_mm_init.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[sg2000_pgalloc.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[sg2000_start.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[sg2000_start.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[sg2000_timerisr.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[sg2000_irq.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[sg2000_irq.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[sg2000_irq.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[sg2000_irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[sg2000_irq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[sg2000_irq_dispatch.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[sg2000_irq_dispatch.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[sg2000_mm_init.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)

## Verification
- Run: `make test`
