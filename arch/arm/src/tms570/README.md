# tms570 (`nuttx/arch/arm/src/tms570`)

## Overview
Hardware abstraction and architecture package for `tms570` (TMS570 Configuration Options; TMS570 Peripheral Support) under `nuttx/arch/arm/src/tms570`, providing 8 header file(s) and 10 source file(s) (including `chip.h`, `tms570_boot.h`, `tms570_clockconfig.h`, `tms570_esm.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/tms570/hardware`, providing 15 header file(s) and 0 source file(s) (including `tms570_esm.h`, `tms570_flash.h`, `tms570_gio.h`, `tms570_iomm.h`).

## Interface
- `[chip.h:ARMV7A_DCACHE_LINESIZE]`
- `[chip.h:ARMV7A_ICACHE_LINESIZE]`
- `[tms570_boot.h:tms570_lowsetup]`
- `[tms570_boot.h:tms570_board_initialize]`
- `[tms570_clockconfig.h:tms570_clockconfig]`
- `[tms570_esm.h:tms570_esm_initialize]`
- `[tms570_esm.h:tms570_esm_interrupt]`
- `[tms570_gio.h:tms570_gio_initialize]`
- `[tms570_gio.h:tms570_gioirq_initialize]`
- `[tms570_gio.h:tms570_configgio]`
- `[tms570_gio.h:tms570_giowrite]`
- `[tms570_gio.h:tms570_gioread]`
- `[tms570_gio.h:tms570_gioirq]`
- `[tms570_gio.h:tms570_gioirqenable]`
- `[tms570_gio.h:tms570_gioirqdisable]`
- `[tms570_gio.h:tms570_dumpgio]`
- `[tms570_gio.h:gio_pinset_t]`
- `[tms570_gio.h:GIO_MODE_SHIFT]`
- `[tms570_gio.h:GIO_MODE_MASK]`
- `[tms570_gio.h:GIO_INPUT]`
- `[tms570_gio.h:GIO_OUTPUT]`
- `[tms570_gio.h:GIO_CFG_SHIFT]`
- `[tms570_gio.h:GIO_CFG_MASK]`
- `[tms570_gio.h:GIO_CFG_DEFAULT]`
- `[tms570_gio.h:GIO_CFG_PULLUP]`
- `[tms570_gio.h:GIO_CFG_PULLDOWN]`
- `[tms570_gio.h:GIO_INT_SHIFT]`
- `[tms570_gio.h:GIO_INT_MASK]`
- `[tms570_gio.h:GIO_INT_NONE]`
- `[tms570_irq.h:up_enable_fiq]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[tms570_boot.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[tms570_boot.c:#error]` Compile-time configuration constraint: CONFIG_ARMV7R_MEMINIT is required by this architecture.
- `[tms570_clockconfig.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[tms570_clockconfig.c:#error]` Compile-time configuration constraint: BOARD_VCLK_DIVIDER is not defined
- `[tms570_esm.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[tms570_gio.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[tms570_gioirq.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[tms570_irq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[tms570_irq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[tms570_lowputc.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[tms570_lowputc.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[tms570_lowputc.c:#error]` Compile-time configuration constraint: No CONFIG_SCIn_SERIAL_CONSOLE Setting

## Side Effects
- `[tms570_boot.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[tms570_boot.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[tms570_clockconfig.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[tms570_clockconfig.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[tms570_esm.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[tms570_esm.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[tms570_gio.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[tms570_gio.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[tms570_gioirq.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[tms570_gioirq.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[tms570_gioirq.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[tms570_gioirq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)

## Verification
- Run: `make test`
