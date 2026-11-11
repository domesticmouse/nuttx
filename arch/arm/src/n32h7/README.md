# n32h7 (`nuttx/arch/arm/src/n32h7`)

## Overview
Hardware abstraction and architecture package for `n32h7` (Timer Configuration; N32H7 TIMx Outputs Configuration) under `nuttx/arch/arm/src/n32h7`, providing 22 header file(s) and 33 source file(s) (including `chip.h`, `n32_capture.h`, `n32_cordic.h`, `n32_dbgmcu.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/n32h7/hardware`, providing 23 header file(s) and 0 source file(s) (including `n32h76x_afio.h`, `n32h76x_dmamux.h`, `n32h76x_gpio.h`, `n32h76x_memorymap.h`).

## Interface
- `[chip.h:ARMV7M_PERIPHERAL_INTERRUPTS]`
- `[chip.h:ARMV7M_DCACHE_LINESIZE]`
- `[chip.h:ARMV7M_ICACHE_LINESIZE]`
- `[n32_capture.h:n32_cap_init]`
- `[n32_capture.h:n32_cap_deinit]`
- `[n32_capture.h:n32_cap_initialize]`
- `[n32_capture.h:n32_cap_dev_s]`
- `[n32_capture.h:n32_cap_ops_s]`
- `[n32_capture.h:n32_cap_ch_cfg_t]`
- `[n32_capture.h:n32_cap_smc_cfg_t]`
- `[n32_capture.h:n32_cap_flags_t]`
- `[n32_capture.h:N32_CAP_SETSMC]`
- `[n32_capture.h:N32_CAP_SETCLOCK]`
- `[n32_capture.h:N32_CAP_SETCHANNEL]`
- `[n32_capture.h:N32_CAP_GETCAPTURE]`
- `[n32_capture.h:N32_CAP_GETEDGES]`
- `[n32_capture.h:N32_CAP_SETISR]`
- `[n32_capture.h:N32_CAP_ENABLEINT]`
- `[n32_capture.h:N32_CAP_ACKFLAGS]`
- `[n32_capture.h:N32_CAP_GETFLAGS]`
- `[n32_capture.h:N32_CAP_EDGE_MASK]`
- `[n32_capture.h:N32_CAP_EDGE_DISABLED]`
- `[n32_capture.h:N32_CAP_EDGE_RISING]`
- `[n32_cordic.h:n32_cordicinitialize]`
- `[n32_dma.h:n32_dmachannel]`
- `[n32_dma.h:n32_dmafree]`
- `[n32_dma.h:n32_dmasetup]`
- `[n32_dma.h:n32_dmastart]`
- `[n32_dma.h:n32_dmastop]`
- `[n32_dma.h:n32_getchannel]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[n32_allocateheap.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[n32_capture.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[n32_capture_lowerhalf.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[n32_capture_lowerhalf.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[n32_cordic.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[n32_dma.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[n32_dma.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[n32_dma.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[n32_gpio.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[n32_idle.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[n32_irq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[n32_irq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation

## Side Effects
- `[n32_usbhs.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[n32_usbhs.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[n32_capture.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[n32_capture.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[n32_capture.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[n32_capture.c:putreg16]` Mutates 16-bit memory-mapped I/O (MMIO) hardware registers (`putreg16`)
- `[n32_capture.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[n32_capture.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[n32_capture.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[n32_cordic.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[n32_cordic.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[n32_dma.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)

## Verification
- Run: `make test`
