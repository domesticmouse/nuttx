# stm32wb (`nuttx/arch/arm/src/stm32wb`)

## Overview
Hardware abstraction and architecture package for `stm32wb` (STM32WB Configuration Options) under `nuttx/arch/arm/src/stm32wb`, providing 22 header file(s) and 32 source file(s) (including `chip.h`, `stm32.h`, `stm32wb_blehci.h`, `stm32wb_dma.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/stm32wb/hardware`, providing 17 header file(s) and 0 source file(s) (including `stm32_rcc.h`, `stm32wb_crs.h`, `stm32wb_dma.h`, `stm32wb_dmamux.h`).

## Interface
- `[chip.h:ARMV7M_PERIPHERAL_INTERRUPTS]`
- `[chip.h:ARMV7M_DCACHE_LINESIZE]`
- `[chip.h:ARMV7M_ICACHE_LINESIZE]`
- `[stm32wb_blehci.h:stm32_blehci_initialize]`
- `[stm32wb_dma.h:stm32_dmachannel]`
- `[stm32wb_dma.h:stm32_dmafree]`
- `[stm32wb_dma.h:stm32_dmasetup]`
- `[stm32wb_dma.h:stm32_dmastart]`
- `[stm32wb_dma.h:stm32_dmastop]`
- `[stm32wb_dma.h:stm32_dmaresidual]`
- `[stm32wb_dma.h:stm32_dmacapable]`
- `[stm32wb_dma.h:stm32_dmasample]`
- `[stm32wb_dma.h:stm32_dmadump]`
- `[stm32wb_dma.h:stm32_dmaregs_s]`
- `[stm32wb_dma.h:DMA_HANDLE]`
- `[stm32wb_dma.h:DMA_STATUS_TEIF]`
- `[stm32wb_dma.h:DMA_STATUS_HTIF]`
- `[stm32wb_dma.h:DMA_STATUS_TCIF]`
- `[stm32wb_dma.h:DMA_STATUS_ERROR]`
- `[stm32wb_dma.h:DMA_STATUS_SUCCESS]`
- `[stm32wb_exti.h:stm32_gpiosetevent]`
- `[stm32wb_exti.h:stm32_exti_alarm]`
- `[stm32wb_exti.h:stm32_exti_wakeup]`
- `[stm32wb_flash.h:stm32_flash_lock]`
- `[stm32wb_flash.h:stm32_flash_unlock]`
- `[stm32wb_flash.h:stm32_flash_user_optbytes]`
- `[stm32wb_gpio.h:stm32_configgpio]`
- `[stm32wb_gpio.h:stm32_unconfiggpio]`
- `[stm32wb_gpio.h:stm32_gpiowrite]`
- `[stm32wb_gpio.h:stm32_gpioread]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[stm32wb_allocateheap.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[stm32wb_allocateheap.c:#error]` Compile-time configuration constraint: SRAM2a heap memory region is out of it's physical address space
- `[stm32wb_blehci.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[stm32wb_dma.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[stm32wb_dma.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[stm32wb_dma.c:#error]` Compile-time configuration constraint: Configuration error, CONFIG_STM32_DMAMUX not defined!
- `[stm32wb_dumpgpio.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[stm32wb_dumpgpio.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[stm32wb_flash.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[stm32wb_gpio.c:spin_lock_irqsave]` Enforces SMP-safe spinlock and interrupt-masking serialization (`spin_lock_irqsave`)
- `[stm32wb_i2c.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[stm32wb_i2c.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates

## Side Effects
- `[stm32wb_ipcc.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[stm32wb_ipcc.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[stm32wb_rcc.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[stm32wb_rcc.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[stm32wb_dma.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[stm32wb_dma.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[stm32wb_dma.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[stm32wb_dma.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[stm32wb_dumpgpio.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[stm32wb_exti_alarm.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[stm32wb_exti_alarm.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[stm32wb_exti_alarm.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)

## Verification
- Run: `make test`
