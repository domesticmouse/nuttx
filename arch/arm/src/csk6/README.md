# csk6 (`nuttx/arch/arm/src/csk6`)

## Overview
Hardware abstraction and architecture package for `csk6` under `nuttx/arch/arm/src/csk6`, providing 2 header file(s) and 5 source file(s) (including `chip.h`, `csk6_lowputc.h`, `csk6_irq.c`, `csk6_lowputc.c`).

## Interface
- `[chip.h:ARMV8M_PERIPHERAL_INTERRUPTS]`
- `[csk6_lowputc.h:csk6_lowsetup]`
- `[csk6_irq.c:up_irqinitialize]`
- `[csk6_irq.c:up_disable_irq]`
- `[csk6_irq.c:up_enable_irq]`
- `[csk6_irq.c:arm_ack_irq]`
- `[csk6_lowputc.c:arm_lowputc]`
- `[csk6_lowputc.c:csk6_lowsetup]`
- `[csk6_serial.c:arm_serialinit]`
- `[csk6_serial.c:arm_earlyserialinit]`
- `[csk6_start.c:g_idle_topstack]`
- `[csk6_start.c:__start]`
- `[csk6_start.c:HEAP_BASE]`
- `[csk6_timer.c:up_timer_initialize]`
- `[CMakeLists.txt:target_sources]`
- `[Make.defs:CHIP_CSRCS]`

## Invariants
- `[csk6_irq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[csk6_irq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[csk6_irq.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)

## Side Effects
- `[csk6_irq.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[csk6_irq.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[csk6_irq.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[csk6_irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[csk6_irq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[csk6_lowputc.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[csk6_lowputc.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[csk6_start.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)
- `[csk6_timer.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)

## Verification
- Run: `make test`
