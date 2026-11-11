# moxart (`nuttx/arch/arm/src/moxart`)

## Overview
Hardware abstraction and architecture package for `moxart` (MoxART Configuration Options) under `nuttx/arch/arm/src/moxart`, providing 1 header file(s) and 5 source file(s) (including `chip.h`, `moxart_16550.c`, `moxart_idle.c`, `moxart_irq.c`).

## Interface
- `[chip.h:UART0_BASE]`
- `[chip.h:UART_THR]`
- `[chip.h:UART_LSR]`
- `[chip.h:UART_LSR_THRE]`
- `[chip.h:UART_RHR_OFFS]`
- `[chip.h:UART_THR_OFFS]`
- `[chip.h:UART_FCR_OFFS]`
- `[chip.h:UART_RFCR_OFFS]`
- `[chip.h:UART_TFCR_OFFS]`
- `[chip.h:UART_SCR_OFFS]`
- `[chip.h:UART_LCR_OFFS]`
- `[chip.h:UART_LSR_OFFS]`
- `[moxart_16550.c:uart_decodeirq]`
- `[moxart_16550.c:uart_ioctl]`
- `[moxart_idle.c:up_idle]`
- `[moxart_irq.c:up_irqinitialize]`
- `[moxart_irq.c:ftintc010_mask_irq]`
- `[moxart_irq.c:ftintc010_unmask_irq]`
- `[moxart_irq.c:ftintc010_set_trig_mode]`
- `[moxart_irq.c:ftintc010_set_trig_level]`
- `[moxart_irq.c:up_disable_irq]`
- `[moxart_irq.c:up_enable_irq]`
- `[moxart_irq.c:arm_ack_irq]`
- `[moxart_irq.c:arm_decodeirq]`
- `[moxart_systemreset.c:up_systemreset]`
- `[moxart_timer.c:up_timer_initialize]`
- `[Kconfig:CONFIG_UART_MOXA_MODE_REG]`
- `[Kconfig:CONFIG_UART_MOXA_IRQ_STATUS_REG]`
- `[Kconfig:CONFIG_UART_MOXA_SHARED_IRQ]`
- `[Make.defs:CHIP_CSRCS]`

## Invariants
- `[moxart_16550.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[moxart_irq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[moxart_16550.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[moxart_16550.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[moxart_idle.c:nxsched_process_timer]` Advances the NuttX kernel system tick and scheduler timer state (`nxsched_process_timer`)
- `[moxart_irq.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[moxart_irq.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[moxart_irq.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[moxart_irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[moxart_irq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[moxart_systemreset.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[moxart_timer.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[moxart_timer.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[moxart_timer.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)

## Verification
- Run: `make test`
