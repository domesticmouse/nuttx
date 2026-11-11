# mps (`nuttx/arch/arm/src/mps`)

## Overview
Hardware abstraction and architecture package for `mps` (MPS Chip Selection) under `nuttx/arch/arm/src/mps`, providing 3 header file(s) and 6 source file(s) (including `chip.h`, `mps_irq.h`, `mps_userspace.h`, `mps_allocateheap.c`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/mps/hardware`, providing 1 header file(s) and 0 source file(s) (including `mps_memorymap.h`).

## Interface
- `[chip.h:ARMV7M_PERIPHERAL_INTERRUPTS]`
- `[chip.h:ARMV8M_PERIPHERAL_INTERRUPTS]`
- `[mps_irq.h:MPS_IRQ_RESERVED]`
- `[mps_irq.h:MPS_IRQ_NMI]`
- `[mps_irq.h:MPS_IRQ_HARDFAULT]`
- `[mps_irq.h:MPS_IRQ_MEMFAULT]`
- `[mps_irq.h:MPS_IRQ_BUSFAULT]`
- `[mps_irq.h:MPS_IRQ_USAGEFAULT]`
- `[mps_irq.h:MPS_IRQ_SVCALL]`
- `[mps_irq.h:MPS_IRQ_DBGMONITOR]`
- `[mps_irq.h:MPS_IRQ_PENDSV]`
- `[mps_irq.h:MPS_IRQ_SYSTICK]`
- `[mps_irq.h:MPS_IRQ_FIRST]`
- `[mps_userspace.h:mps_userspace]`
- `[mps_allocateheap.c:up_allocate_heap]`
- `[mps_allocateheap.c:up_allocate_kheap]`
- `[mps_allocateheap.c:arm_addregion]`
- `[mps_allocateheap.c:up_textheap_free]`
- `[mps_allocateheap.c:up_textheap_heapmember]`
- `[mps_allocateheap.c:up_dataheap_free]`
- `[mps_allocateheap.c:up_dataheap_heapmember]`
- `[mps_irq.c:up_prioritize_irq]`
- `[mps_irq.c:up_irqinitialize]`
- `[mps_irq.c:up_disable_irq]`
- `[mps_irq.c:up_enable_irq]`
- `[mps_irq.c:arm_ack_irq]`
- `[mps_serial.c:arm_serialinit]`
- `[mps_serial.c:arm_earlyserialinit]`
- `[mps_start.c:g_idle_topstack]`
- `[mps_start.c:mps_tcmenable]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[mps_allocateheap.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[mps_irq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[mps_irq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[mps_irq.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[mps_userspace.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[mps_irq.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[mps_irq.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[mps_irq.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[mps_irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[mps_irq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[mps_start.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[mps_start.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[mps_timer.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)

## Verification
- Run: `make test`
