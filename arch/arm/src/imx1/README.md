# imx1 (`nuttx/arch/arm/src/imx1`)

## Overview
Hardware abstraction and architecture package for `imx1` (iMX.1 Peripheral Selection) under `nuttx/arch/arm/src/imx1`, providing 14 header file(s) and 8 source file(s) (including `chip.h`, `imx_aitc.h`, `imx_cspi.h`, `imx_dma.h`).

## Interface
- `[imx_aitc.h:AITC_INTCNTL_OFFSET]`
- `[imx_aitc.h:AITC_NIMASK_OFFSET]`
- `[imx_aitc.h:AITC_INTENNUM_OFFSET]`
- `[imx_aitc.h:AITC_INTDISNUM_OFFSET]`
- `[imx_aitc.h:AITC_INTENABLEH_OFFSET]`
- `[imx_aitc.h:AITC_INTENABLEL_OFFSET]`
- `[imx_aitc.h:AITC_INTTYPEH_OFFSET]`
- `[imx_aitc.h:AITC_INTTYPEL_OFFSET]`
- `[imx_aitc.h:AITC_NIPRIORITY7_OFFSET]`
- `[imx_aitc.h:AITC_NIPRIORITY6_OFFSET]`
- `[imx_aitc.h:AITC_NIPRIORITY5_OFFSET]`
- `[imx_aitc.h:AITC_NIPRIORITY4_OFFSET]`
- `[imx_cspi.h:imx_spibus_initialize]`
- `[imx_cspi.h:imx_spiselect]`
- `[imx_cspi.h:imx_spistatus]`
- `[imx_cspi.h:imx_spicmddata]`
- `[imx_cspi.h:CSPI_RXD_OFFSET]`
- `[imx_cspi.h:CSPI_TXD_OFFSET]`
- `[imx_cspi.h:CSPI_CTRL_OFFSET]`
- `[imx_cspi.h:CSPI_INTCS_OFFSET]`
- `[imx_cspi.h:CSPI_TEST_OFFSET]`
- `[imx_cspi.h:CSPI_SPCR_OFFSET]`
- `[imx_cspi.h:CSPI_DMA_OFFSET]`
- `[imx_cspi.h:CSPI_RESET_OFFSET]`
- `[imx_cspi.h:IMX_CSPI1_RXD]`
- `[imx_cspi.h:IMX_CSPI1_TXD]`
- `[imx_cspi.h:IMX_CSPI1_CTRL]`
- `[imx_cspi.h:IMX_CSPI1_INTCS]`
- `[imx_dma.h:DMA_SYS_OFFSET]`
- `[imx_dma.h:DMA_M2D_OFFSET]`

## Invariants
- `[imx_memorymap.h:#error]` Compile-time guard: CONFIG_RAM_NUTTXENTRY does not have correct offset for page table
- `[imx_decodeirq.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[imx_decodeirq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[imx_serial.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[imx_serial.c:#error]` Compile-time configuration constraint: No UARTs enabled
- `[imx_spi.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[imx_spi.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates

## Side Effects
- `[imx_gpio.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[imx_gpio.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[imx_decodeirq.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[imx_irq.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[imx_irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[imx_irq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[imx_serial.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[imx_serial.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[imx_serial.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[imx_serial.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[imx_serial.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[imx_spi.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)

## Verification
- Run: `make test`
