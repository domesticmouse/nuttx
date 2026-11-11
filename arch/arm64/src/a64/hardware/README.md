# hardware (`nuttx/arch/arm64/src/a64/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm64/src/a64/hardware`, providing 3 header file(s) and 0 source file(s) (including `a64_memorymap.h`, `a64_pio.h`, `a64_twi.h`).

## Interface
- `[a64_memorymap.h:A64_DE_ADDR]`
- `[a64_memorymap.h:A64_SYSCTL_ADDR]`
- `[a64_memorymap.h:A64_TCON0_ADDR]`
- `[a64_memorymap.h:A64_CCU_ADDR]`
- `[a64_memorymap.h:A64_PIO_ADDR]`
- `[a64_memorymap.h:A64_PWM_ADDR]`
- `[a64_memorymap.h:A64_UART0_ADDR]`
- `[a64_memorymap.h:A64_UART1_ADDR]`
- `[a64_memorymap.h:A64_UART2_ADDR]`
- `[a64_memorymap.h:A64_UART3_ADDR]`
- `[a64_memorymap.h:A64_UART4_ADDR]`
- `[a64_memorymap.h:A64_TWI0_ADDR]`
- `[a64_pio.h:PIO_REG_PORTB]`
- `[a64_pio.h:PIO_REG_PORTC]`
- `[a64_pio.h:PIO_REG_PORTD]`
- `[a64_pio.h:PIO_REG_PORTE]`
- `[a64_pio.h:PIO_REG_PORTF]`
- `[a64_pio.h:PIO_REG_PORTG]`
- `[a64_pio.h:PIO_REG_PORTH]`
- `[a64_pio.h:PIO_REG_PORTL]`
- `[a64_pio.h:PIO_REG_CFG_INPUT]`
- `[a64_pio.h:PIO_REG_CFG_OUTPUT]`
- `[a64_pio.h:PIO_REG_DRV_LEVEL0]`
- `[a64_pio.h:PIO_REG_DRV_LEVEL1]`
- `[a64_twi.h:A64_TWI_ADDR_OFFSET]`
- `[a64_twi.h:A64_TWI_XADDR_OFFSET]`
- `[a64_twi.h:A64_TWI_DATA_OFFSET]`
- `[a64_twi.h:A64_TWI_CNTR_OFFSET]`
- `[a64_twi.h:A64_TWI_STAT_OFFSET]`
- `[a64_twi.h:A64_TWI_CCR_OFFSET]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
