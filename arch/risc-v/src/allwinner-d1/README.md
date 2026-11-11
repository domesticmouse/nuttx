# allwinner-d1 (`nuttx/arch/risc-v/src/allwinner-d1`)

## Overview
Hardware abstraction and architecture package for `allwinner-d1` under `nuttx/arch/risc-v/src/allwinner-d1`, providing 2 header file(s) and 4 source file(s) (including `allwinner_d1_memorymap.h`, `chip.h`, `allwinner_d1_irq.c`, `allwinner_d1_irq_dispatch.c`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/risc-v/src/allwinner-d1/hardware`, providing 4 header file(s) and 0 source file(s) (including `allwinner_d1_memorymap.h`, `allwinner_d1_plic.h`, `allwinner_d1_timer.h`, `allwinner_d1_wdt.h`).

## Interface
- `[allwinner_d1_memorymap.h:ALLWINNER_D1_IDLESTACK_BASE]`
- `[allwinner_d1_irq.c:up_irqinitialize]`
- `[allwinner_d1_irq.c:up_disable_irq]`
- `[allwinner_d1_irq.c:up_enable_irq]`
- `[allwinner_d1_irq.c:up_irq_enable]`
- `[allwinner_d1_irq_dispatch.c:riscv_dispatch_irq]`
- `[allwinner_d1_start.c:allwinner_d1_start]`
- `[allwinner_d1_start.c:riscv_earlyserialinit]`
- `[allwinner_d1_start.c:riscv_serialinit]`
- `[allwinner_d1_timerisr.c:up_timer_initialize]`
- `[Make.defs:CHIP_CSRCS]`
- `[Make.defs:HEAD_ASRC]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[allwinner_d1_irq.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[allwinner_d1_timerisr.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[allwinner_d1_timerisr.c:#error]` Compile-time configuration constraint: The D1 timer requires an integer number of counts per tick

## Side Effects
- `[allwinner_d1_irq.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[allwinner_d1_irq.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[allwinner_d1_irq.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[allwinner_d1_irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[allwinner_d1_irq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[allwinner_d1_irq_dispatch.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[allwinner_d1_irq_dispatch.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[allwinner_d1_start.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[allwinner_d1_start.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[allwinner_d1_start.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[allwinner_d1_timerisr.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[allwinner_d1_timerisr.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)

## Verification
- Run: `make test`
