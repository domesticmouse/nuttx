# gd32f4 (`nuttx/arch/arm/src/gd32f4`)

## Overview
Hardware abstraction and architecture package for `gd32f4` (GD32F4 Configuration Options; GD32 Peripheral Support) under `nuttx/arch/arm/src/gd32f4`, providing 17 header file(s) and 19 source file(s) (including `chip.h`, `gd32f4xx.h`, `gd32f4xx_dma.h`, `gd32f4xx_enet.h`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/gd32f4/hardware`, providing 16 header file(s) and 0 source file(s) (including `gd32f450_memorymap.h`, `gd32f450_pinmap.h`, `gd32f4xx_dma.h`, `gd32f4xx_enet.h`).

## Interface
- `[chip.h:ARMV7M_PERIPHERAL_INTERRUPTS]`
- `[gd32f4xx_dma.h:gd32_dma_channel_alloc]`
- `[gd32f4xx_dma.h:gd32_dma_channel_free]`
- `[gd32f4xx_dma.h:gd32_dma_setup]`
- `[gd32f4xx_dma.h:gd32_dma_start]`
- `[gd32f4xx_dma.h:gd32_dma_stop]`
- `[gd32f4xx_dma.h:gd32_dma_tansnum_get]`
- `[gd32f4xx_dma.h:gd32_dma_sample]`
- `[gd32f4xx_dma.h:gd32_dma_dump]`
- `[gd32f4xx_dma.h:gd32_dmaregs_s]`
- `[gd32f4xx_dma.h:dma_single_data_parameter_struct]`
- `[gd32f4xx_dma.h:DMA_HANDLE]`
- `[gd32f4xx_dma.h:DMA_STATUS_ERROR]`
- `[gd32f4xx_dma.h:DMA_STATUS_SUCCESS]`
- `[gd32f4xx_dma.h:DMA_INTF_MASK]`
- `[gd32f4xx_dma.h:DMA_INT_MASK]`
- `[gd32f4xx_dma.h:GD32_DMA0]`
- `[gd32f4xx_dma.h:GD32_DMA1]`
- `[gd32f4xx_enet.h:gd32_phy_boardinitialize]`
- `[gd32f4xx_exti.h:gd32_exti_gpioirq_init]`
- `[gd32f4xx_exti.h:gd32_exti_gpio_irq_attach]`
- `[gd32f4xx_exti.h:gd32_exti_init]`
- `[gd32f4xx_exti.h:gd32_gpio_exti_linex_get]`
- `[gd32f4xx_exti.h:gd32_gpio_exti_irqnum_get]`
- `[gd32f4xx_exti.h:gd32_exti_interrupt_enable]`
- `[gd32f4xx_exti.h:gd32_exti_event_enable]`
- `[gd32f4xx_exti.h:gd32_exti_event_disable]`
- `[gd32f4xx_exti.h:gd32_exti_software_interrupt_enable]`
- `[gd32f4xx_exti.h:gd32_exti_software_interrupt_disable]`
- `[gd32f4xx_exti.h:gd32_exti_interrupt_flag_get]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- `[gd32f4xx_gpio.h:#error]` Compile-time guard: Unknown GD32 chip
- `[gd32f4xx_rcu.h:#error]` Compile-time guard: Unknown GD32 chip
- `[gd32f4xx_syscfg.h:#error]` Compile-time guard: Unknown GD32 Chip
- `[gd32f4xx_usart.h:#error]` Compile-time guard: Unsupported GD32 UART
- `[gd32f4xx_allocateheap.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[gd32f4xx_allocateheap.c:#error]` Compile-time configuration constraint: There is at least one memory region
- `[gd32f4xx_dma.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[gd32f4xx_dma.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[gd32f4xx_enet.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[gd32f4xx_enet.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[gd32f4xx_enet.c:#error]` Compile-time configuration constraint: Logic to support multiple Ethernet interfaces is incomplete
- `[gd32f4xx_gpio.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates

## Side Effects
- `[gd32f4xx_dma.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[gd32f4xx_dma.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[gd32f4xx_dma.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[gd32f4xx_dma.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[gd32f4xx_dma.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[gd32f4xx_enet.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[gd32f4xx_enet.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[gd32f4xx_enet.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[gd32f4xx_enet.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[gd32f4xx_enet.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[gd32f4xx_enet.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[gd32f4xx_exti.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)

## Verification
- Run: `make test`
