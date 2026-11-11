# erbium (`nuttx/arch/risc-v/src/erbium`)

## Overview
Hardware abstraction and architecture package for `erbium` under `nuttx/arch/risc-v/src/erbium`, providing 3 header file(s) and 6 source file(s) (including `chip.h`, `erbium_mcode.h`, `erbium_memorymap.h`, `erbium_irq.c`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/risc-v/src/erbium/hardware`, providing 5 header file(s) and 0 source file(s) (including `erbium_memorymap.h`, `erbium_mtimer.h`, `erbium_plic.h`, `erbium_sysreg.h`).

## Interface
- `[erbium_mcode.h:erbium_mcode_emulate]`
- `[erbium_mcode.h:erbium_mcode_getfpr]`
- `[erbium_mcode.h:erbium_mcode_setfpr]`
- `[erbium_memorymap.h:ERBIUM_IDLESTACK_BASE]`
- `[erbium_memorymap.h:ERBIUM_IDLESTACK_SIZE]`
- `[erbium_memorymap.h:ERBIUM_IDLESTACK_TOP]`
- `[erbium_irq.c:up_irqinitialize]`
- `[erbium_irq.c:up_disable_irq]`
- `[erbium_irq.c:up_enable_irq]`
- `[erbium_irq.c:up_irq_enable]`
- `[erbium_irq_dispatch.c:riscv_dispatch_irq]`
- `[erbium_mcode.c:erbium_mcode_emulate]`
- `[erbium_serial.c:riscv_earlyserialinit]`
- `[erbium_serial.c:riscv_serialinit]`
- `[erbium_serial.c:up_putc]`
- `[erbium_start.c:erbium_start]`
- `[erbium_timerisr.c:up_timer_initialize]`
- `[CMakeLists.txt:target_sources]`
- `[Kconfig:CONFIG_ERBIUM_UART_CLOCK]`
- `[Kconfig:CONFIG_ERBIUM_MTIMER_FREQ]`
- `[Kconfig:CONFIG_ERBIUM_MCODE_EMULATION]`
- `[Make.defs:CHIP_CSRCS]`
- `[Make.defs:HEAD_ASRC]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[erbium_irq.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[erbium_irq.c:static_assert]` Enforces compile-time size and alignment invariants via `static_assert`
- `[erbium_irq_dispatch.c:#error]` Compile-time configuration constraint: ET-Minion exception codes would alias interrupt IRQ numbers
- `[erbium_mcode.c:static_assert]` Enforces compile-time size and alignment invariants via `static_assert`
- `[erbium_serial.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[erbium_serial.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[erbium_serial.c:#error]` Compile-time configuration constraint: The Erbium UART driver supports only 8N1
- `[erbium_timerisr.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[erbium_irq.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[erbium_irq.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[erbium_irq.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[erbium_irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[erbium_irq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[erbium_irq_dispatch.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[erbium_irq_dispatch.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[erbium_mcode.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)
- `[erbium_serial.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[erbium_serial.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[erbium_serial.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[erbium_serial.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)

## Verification
- Run: `make test`
