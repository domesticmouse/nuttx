# stm32n6 (`nuttx/arch/arm/src/stm32n6`)

## Overview
Hardware abstraction and architecture package for `stm32n6` (STM32N6 Configuration Options) under `nuttx/arch/arm/src/stm32n6`, providing 5 header file(s) and 6 source file(s) (including `chip.h`, `stm32.h`, `stm32_pwr.h`, `stm32_rcc.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/stm32n6/hardware`, providing 12 header file(s) and 0 source file(s) (including `stm32_dmasigmap.h`, `stm32_memorymap.h`, `stm32_pinmap.h`, `stm32_rcc.h`).

## Interface
- `[chip.h:ARMV8M_PERIPHERAL_INTERRUPTS]`
- `[chip.h:ARMV8M_ICACHE_LINESIZE]`
- `[chip.h:ARMV8M_DCACHE_LINESIZE]`
- `[chip.h:STM32_DMA1_NCHAN]`
- `[chip.h:STM32_DMA1_IRQ_FIRST]`
- `[chip.h:STM32_DMA2_NCHAN]`
- `[chip.h:STM32_DMA2_IRQ_FIRST]`
- `[stm32_pwr.h:stm32_pwr_enablebkp]`
- `[stm32_pwr.h:stm32_pwr_enablevddio]`
- `[stm32_rcc.h:stm32_clockconfig]`
- `[stm32_rcc.h:stm32_stdclockconfig]`
- `[stm32_rcc.h:stm32_clockenable]`
- `[stm32_rcc.h:stm32_rcc_enableperipherals]`
- `[stm32_rcc.h:stm32_rcc_enablelse]`
- `[stm32_rcc.h:stm32_rcc_enablelsi]`
- `[stm32_rcc.h:STM32_LPUART1_RCC_REG]`
- `[stm32_rcc.h:STM32_LPUART1_RCC_EN]`
- `[stm32_rcc.h:STM32_USART1_RCC_REG]`
- `[stm32_rcc.h:STM32_USART1_RCC_EN]`
- `[stm32_rcc.h:STM32_USART2_RCC_REG]`
- `[stm32_rcc.h:STM32_USART2_RCC_EN]`
- `[stm32_rcc.h:STM32_USART3_RCC_REG]`
- `[stm32_rcc.h:STM32_USART3_RCC_EN]`
- `[stm32_rcc.h:STM32_UART4_RCC_REG]`
- `[stm32_rcc.h:STM32_UART4_RCC_EN]`
- `[stm32_rcc.h:STM32_UART5_RCC_REG]`
- `[stm32_rcc.h:STM32_UART5_RCC_EN]`
- `[stm32_start.h:stm32_board_initialize]`
- `[stm32_idle.c:up_idle]`
- `[stm32_irq.c:up_irqinitialize]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[stm32_irq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[stm32_irq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[stm32_irq.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[stm32_irq.c:up_irq_save]` Preserves local interrupt mask state across atomic hardware operations (`up_irq_save` / `up_irq_restore`)
- `[stm32n6xx_rcc.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`

## Side Effects
- `[stm32_idle.c:nxsched_process_timer]` Advances the NuttX kernel system tick and scheduler timer state (`nxsched_process_timer`)
- `[stm32_irq.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[stm32_irq.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[stm32_irq.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[stm32_irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[stm32_irq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[stm32_pwr.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[stm32_pwr.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[stm32_pwr.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[stm32_start.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[stm32_start.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[stm32_start.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)

## Verification
- Run: `make test`
