# jh7110 (`nuttx/arch/risc-v/src/jh7110`)

## Overview
Hardware abstraction and architecture package for `jh7110` under `nuttx/arch/risc-v/src/jh7110`, providing 3 header file(s) and 7 source file(s) (including `chip.h`, `jh7110_memorymap.h`, `jh7110_mm_init.h`, `jh7110_allocateheap.c`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/risc-v/src/jh7110/hardware`, providing 2 header file(s) and 0 source file(s) (including `jh7110_memorymap.h`, `jh7110_plic.h`).

## Interface
- `[jh7110_memorymap.h:JH7110_IDLESTACK_BASE]`
- `[jh7110_mm_init.h:jh7110_kernel_mappings]`
- `[jh7110_mm_init.h:jh7110_mm_init]`
- `[jh7110_allocateheap.c:up_allocate_kheap]`
- `[jh7110_irq.c:up_irqinitialize]`
- `[jh7110_irq.c:up_disable_irq]`
- `[jh7110_irq.c:up_enable_irq]`
- `[jh7110_irq.c:up_irq_enable]`
- `[jh7110_irq_dispatch.c:riscv_dispatch_irq]`
- `[jh7110_mm_init.c:jh7110_kernel_mappings]`
- `[jh7110_mm_init.c:jh7110_mm_init]`
- `[jh7110_pgalloc.c:up_allocate_pgheap]`
- `[jh7110_start.c:jh7110_clear_bss]`
- `[jh7110_start.c:jh7110_start_s]`
- `[jh7110_start.c:jh7110_start]`
- `[jh7110_start.c:riscv_earlyserialinit]`
- `[jh7110_start.c:riscv_serialinit]`
- `[jh7110_timerisr.c:up_timer_initialize]`
- `[Make.defs:CHIP_CSRCS]`
- `[Make.defs:HEAD_ASRC]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[jh7110_irq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[jh7110_irq.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[jh7110_mm_init.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[jh7110_pgalloc.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[jh7110_start.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[jh7110_irq.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[jh7110_irq.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[jh7110_irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[jh7110_irq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[jh7110_irq_dispatch.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[jh7110_irq_dispatch.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[jh7110_timerisr.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[jh7110_timerisr.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[jh7110_timerisr.c:nxsched_process_timer]` Advances the NuttX kernel system tick and scheduler timer state (`nxsched_process_timer`)

## Verification
- Run: `make test`
