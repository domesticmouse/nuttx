# lpc214x (`nuttx/arch/arm/src/lpc214x`)

## Overview
Hardware abstraction and architecture package for `lpc214x` (LPC214x Configuration Options; LPC214x Initialization Options) under `nuttx/arch/arm/src/lpc214x`, providing 11 header file(s) and 5 source file(s) (including `chip.h`, `lpc214x_apb.h`, `lpc214x_i2c.h`, `lpc214x_pinsel.h`).

## Interface
- `[chip.h:LPC214X_FLASH_BASE]`
- `[chip.h:LPC214X_FIO_BASE]`
- `[chip.h:LPC214X_ONCHIP_RAM_BASE]`
- `[chip.h:LPC214X_USBDMA_RAM_BASE]`
- `[chip.h:LPC214X_BOOT_BLOCK]`
- `[chip.h:LPC214X_EXTMEM_BASE]`
- `[chip.h:LPC214X_APB_BASE]`
- `[chip.h:LPC214X_AHB_BASE]`
- `[chip.h:LPC214X_FIO0_BASE]`
- `[chip.h:LPC214X_FIO1_BASE]`
- `[chip.h:LPC214X_WD_BASE]`
- `[chip.h:LPC214X_TMR0_BASE]`
- `[lpc214x_apb.h:LPC214X_APB_APBDIV]`
- `[lpc214x_apb.h:LPC214X_APBDIV_MASK]`
- `[lpc214x_apb.h:LPC214X_APBDIV_DIV4]`
- `[lpc214x_apb.h:LPC214X_APBDIV_DIV1]`
- `[lpc214x_apb.h:LPC214X_APBDIV_DIV2]`
- `[lpc214x_i2c.h:LPC214X_I2C0_CONSET]`
- `[lpc214x_i2c.h:LPC214X_I2C0_STAT]`
- `[lpc214x_i2c.h:LPC214X_I2C0_DAT]`
- `[lpc214x_i2c.h:LPC214X_I2C0_ADR]`
- `[lpc214x_i2c.h:LPC214X_I2C0_SCLH]`
- `[lpc214x_i2c.h:LPC214X_I2C0_SCLL]`
- `[lpc214x_i2c.h:LPC214X_I2C0_CONCLR]`
- `[lpc214x_i2c.h:LPC214X_I2C1_CONSET]`
- `[lpc214x_i2c.h:LPC214X_I2C1_STAT]`
- `[lpc214x_i2c.h:LPC214X_I2C1_DAT]`
- `[lpc214x_i2c.h:LPC214X_I2C1_ADR]`
- `[lpc214x_i2c.h:LPC214X_I2C1_SCLH]`
- `[lpc214x_pinsel.h:LPC214X_PINSEL0]`

## Invariants
- `[lpc214x_decodeirq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[lpc214x_irq.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[lpc214x_serial.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[lpc214x_serial.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[lpc214x_serial.c:#error]` Compile-time configuration constraint: No CONFIG_UARTn_SERIAL_CONSOLE Setting
- `[lpc214x_usbdev.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[lpc214x_usbdev.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[lpc214x_usbdev.c:#error]` Compile-time configuration constraint: DMA SUPPORT NOT YET FULLY IMPLEMENTED

## Side Effects
- `[lpc214x_vic.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[lpc214x_vic.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[lpc214x_irq.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[lpc214x_irq.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[lpc214x_serial.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[lpc214x_serial.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[lpc214x_serial.c:putreg8]` Mutates 8-bit memory-mapped I/O (MMIO) hardware registers (`putreg8`)
- `[lpc214x_serial.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)
- `[lpc214x_serial.c:up_enable_irq]` Enables hardware interrupt lines in the interrupt controller (`up_enable_irq`)
- `[lpc214x_serial.c:up_disable_irq]` Disables hardware interrupt lines in the interrupt controller (`up_disable_irq`)
- `[lpc214x_timerisr.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[lpc214x_timerisr.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)

## Verification
- Run: `make test`
