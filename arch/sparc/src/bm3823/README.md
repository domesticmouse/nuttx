# bm3823 (`nuttx/arch/sparc/src/bm3823`)

## Overview
Hardware abstraction and architecture package for `bm3823` (BM3823 Configuration Options; BM3823 Peripheral Support) under `nuttx/arch/sparc/src/bm3823`, providing 5 header file(s) and 5 source file(s) (including `bm3823-config.h`, `bm3823-memorymap.h`, `bm3823-uart.h`, `bm3823.h`).

## Interface
- `[bm3823-config.h:HAVE_UART_DEVICE]`
- `[bm3823-config.h:HAVE_SERIAL_CONSOLE]`
- `[bm3823-memorymap.h:BM3823_INTER_REG_BASE]`
- `[bm3823-memorymap.h:BM3823_EXTER_REG_BASE]`
- `[bm3823-memorymap.h:BM3823_UART1_BASE]`
- `[bm3823-memorymap.h:BM3823_UART2_BASE]`
- `[bm3823-memorymap.h:BM3823_UART3_BASE]`
- `[bm3823-memorymap.h:BM3823_UART4_BASE]`
- `[bm3823-uart.h:BM3823_UART_TXREG_OFFSET]`
- `[bm3823-uart.h:BM3823_UART_RXREG_OFFSET]`
- `[bm3823-uart.h:BM3823_UART_STATREG_OFFSET]`
- `[bm3823-uart.h:BM3823_UART_CTRLREG_OFFSET]`
- `[bm3823-uart.h:BM3823_UART_SCALREG_OFFSET]`
- `[bm3823-uart.h:BM3823_UART1_TXREG]`
- `[bm3823-uart.h:BM3823_UART1_RXREG]`
- `[bm3823-uart.h:BM3823_UART1_STATREG]`
- `[bm3823-uart.h:BM3823_UART1_CTRLREG]`
- `[bm3823-uart.h:BM3823_UART1_SCALREG]`
- `[bm3823-uart.h:BM3823_UART2_TXREG]`
- `[bm3823-uart.h:BM3823_UART2_RXREG]`
- `[bm3823.h:up_clkinitialize]`
- `[bm3823.h:usart1_reset]`
- `[bm3823.h:usart2_reset]`
- `[bm3823.h:usart3_reset]`
- `[bm3823.h:uart1_configure]`
- `[bm3823.h:uart2_configure]`
- `[bm3823.h:uart3_configure]`
- `[bm3823.h:sparc_consoleinit]`
- `[bm3823.h:bm3823_uartconfigure]`
- `[bm3823.h:bm3823_boardinitialize]`

## Invariants
- `[chip.h:#error]` Compile-time guard: Unsupported SPARC chip
- `[bm3823-irq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[bm3823-serial.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[bm3823-serial.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[bm3823-serial.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[bm3823-serial.c:#error]` Compile-time configuration constraint: I'm confused... Do we have a serial console or not?

## Side Effects
- `[bm3823.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[bm3823-irq.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[bm3823-irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[bm3823-irq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[bm3823-serial.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[bm3823-serial.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[bm3823-serial.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[bm3823-serial.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[bm3823-timerisr.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[bm3823-timerisr.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[bm3823-timerisr.c:nxsched_process_timer]` Advances the NuttX kernel system tick and scheduler timer state (`nxsched_process_timer`)

## Verification
- Run: `make test`
