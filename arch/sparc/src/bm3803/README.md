# bm3803 (`nuttx/arch/sparc/src/bm3803`)

## Overview
Hardware abstraction and architecture package for `bm3803` (BM3803 Configuration Options; BM3803 Peripheral Support) under `nuttx/arch/sparc/src/bm3803`, providing 10 header file(s) and 13 source file(s) (including `bm3803-config.h`, `bm3803-memorymap.h`, `bm3803-uart.h`, `bm3803.h`).

## Interface
- `[bm3803-config.h:HAVE_UART_DEVICE]`
- `[bm3803-config.h:HAVE_SERIAL_CONSOLE]`
- `[bm3803-memorymap.h:BM3803_REG_BASE]`
- `[bm3803-memorymap.h:BM3803_UART1_BASE]`
- `[bm3803-memorymap.h:BM3803_UART2_BASE]`
- `[bm3803-memorymap.h:BM3803_UART3_BASE]`
- `[bm3803-uart.h:BM3803_UART_TXREG_OFFSET]`
- `[bm3803-uart.h:BM3803_UART_RXREG_OFFSET]`
- `[bm3803-uart.h:BM3803_UART_STATREG_OFFSET]`
- `[bm3803-uart.h:BM3803_UART_CTRLREG_OFFSET]`
- `[bm3803-uart.h:BM3803_UART_SCALREG_OFFSET]`
- `[bm3803-uart.h:BM3803_UART1_TXREG]`
- `[bm3803-uart.h:BM3803_UART1_RXREG]`
- `[bm3803-uart.h:BM3803_UART1_STATREG]`
- `[bm3803-uart.h:BM3803_UART1_CTRLREG]`
- `[bm3803-uart.h:BM3803_UART1_SCALREG]`
- `[bm3803-uart.h:BM3803_UART2_TXREG]`
- `[bm3803-uart.h:BM3803_UART2_RXREG]`
- `[bm3803.h:up_clkinitialize]`
- `[bm3803.h:usart1_reset]`
- `[bm3803.h:usart2_reset]`
- `[bm3803.h:usart3_reset]`
- `[bm3803.h:uart1_configure]`
- `[bm3803.h:uart2_configure]`
- `[bm3803.h:uart3_configure]`
- `[bm3803.h:sparc_consoleinit]`
- `[bm3803.h:bm3803_uartconfigure]`
- `[bm3803.h:bm3803_boardinitialize]`
- `[bm3803.h:gpio_irqinitialize]`
- `[bm3803.h:gpio_irqattach]`

## Invariants
- `[chip.h:#error]` Compile-time guard: Unsupported SPARC chip
- `[bm3803-irq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[bm3803-serial.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[bm3803-serial.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[bm3803-serial.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[bm3803-serial.c:#error]` Compile-time configuration constraint: I'm confused... Do we have a serial console or not?
- `[bm3803_freerun.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[bm3803_freerun.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[bm3803_oneshot.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[bm3803_oneshot.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[bm3803_oneshot_lowerhalf.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[bm3803_oneshot_lowerhalf.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates

## Side Effects
- `[bm3803.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations
- `[bm3803-irq.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[bm3803-irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[bm3803-irq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[bm3803-serial.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[bm3803-serial.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[bm3803-serial.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[bm3803-serial.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[bm3803-timerisr.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[bm3803-timerisr.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[bm3803-timerisr.c:nxsched_process_timer]` Advances the NuttX kernel system tick and scheduler timer state (`nxsched_process_timer`)
- `[bm3803_exti_gpio.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)

## Verification
- Run: `make test`
