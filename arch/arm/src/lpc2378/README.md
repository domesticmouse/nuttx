# lpc2378 (`nuttx/arch/arm/src/lpc2378`)

## Overview
Hardware abstraction and architecture package for `lpc2378` (LPC2378 Configuration Options; LPC2378 Peripheral Support) under `nuttx/arch/arm/src/lpc2378`, providing 10 header file(s) and 8 source file(s) (including `chip.h`, `lpc2378.h`, `lpc23xx_gpio.h`, `lpc23xx_i2c.h`).

## Interface
- `[chip.h:LPC23XX_FLASH_BASE]`
- `[chip.h:LPC23XX_FIO_BASE]`
- `[chip.h:LPC23XX_ONCHIP_RAM_BASE]`
- `[chip.h:LPC23XX_USBDMA_RAM_BASE]`
- `[chip.h:LPC23XX_ETHERNET_RAM_BASE]`
- `[chip.h:LPC23XX_BOOT_BLOCK]`
- `[chip.h:LPC23XX_EXTMEM_BASE]`
- `[chip.h:LPC23XX_APB_BASE]`
- `[chip.h:LPC23XX_AHB_BASE]`
- `[chip.h:LPC23XX_WD_BASE]`
- `[chip.h:LPC23XX_TMR0_BASE]`
- `[chip.h:LPC23XX_TMR1_BASE]`
- `[lpc2378.h:lpc2378_statledoff]`
- `[lpc2378.h:lpc2378_statledon]`
- `[lpc23xx_gpio.h:io_getreg8]`
- `[lpc23xx_gpio.h:io_getreg]`
- `[lpc23xx_gpio.h:dir_getreg8]`
- `[lpc23xx_gpio.h:dir_getreg]`
- `[lpc23xx_gpio.h:dir_putreg8]`
- `[lpc23xx_gpio.h:dir_putreg]`
- `[lpc23xx_gpio.h:fio_putreg8]`
- `[lpc23xx_gpio.h:fio_getreg8]`
- `[lpc23xx_i2c.h:lpc2378_i2cbus_initialize]`
- `[lpc23xx_i2c.h:lpc2378_i2cbus_uninitialize]`
- `[lpc23xx_i2c.h:I2C0_PCLKSEL_MASK]`
- `[lpc23xx_i2c.h:I2C1_PCLKSEL_MASK]`
- `[lpc23xx_i2c.h:I2C2_PCLKSEL_MASK]`
- `[lpc23xx_i2c.h:I2C0_PCLKSEL]`
- `[lpc23xx_i2c.h:I2C1_PCLKSEL]`
- `[lpc23xx_i2c.h:I2C2_PCLKSEL]`

## Invariants
- `[lpc23xx_uart.h:#error]` Compile-time guard: UART0 PCLK divider not set
- `[lpc23xx_decodeirq.c:PANIC]` Halts execution via kernel `PANIC` on unrecoverable hardware or state invariant violation
- `[lpc23xx_i2c.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[lpc23xx_i2c.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[lpc23xx_irq.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[lpc23xx_pllsetup.c:#error]` Compile-time configuration constraint: Fosc out of range (32KHz-50MHz)
- `[lpc23xx_serial.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[lpc23xx_serial.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[lpc23xx_serial.c:#error]` Compile-time configuration constraint: No CONFIG_UARTn_SERIAL_CONSOLE Setting
- `[lpc23xx_spi.c:DEBUGASSERT]` Enforces runtime precondition and state assertions via `DEBUGASSERT`
- `[lpc23xx_spi.c:enter_critical_section]` Requires critical section serialization (`enter_critical_section` / `leave_critical_section`) across state and register updates
- `[lpc23xx_spi.c:#error]` Compile-time configuration constraint: CONFIG_SPI_EXCHANGE is not supported by this driver

## Side Effects
- `[lpc23xx_gpio.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[lpc23xx_gpio.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[lpc23xx_pinsel.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[lpc23xx_pinsel.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[lpc23xx_scb.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[lpc23xx_scb.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[lpc23xx_timer.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[lpc23xx_timer.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[lpc23xx_vic.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers
- `[lpc23xx_vic.h:getreg32]` Reads 32-bit values from memory-mapped I/O (MMIO) peripheral registers
- `[lpc23xx_i2c.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[lpc23xx_i2c.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)

## Verification
- Run: `make test`
