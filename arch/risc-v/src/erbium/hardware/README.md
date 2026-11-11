# hardware (`nuttx/arch/risc-v/src/erbium/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/risc-v/src/erbium/hardware`, providing 5 header file(s) and 0 source file(s) (including `erbium_memorymap.h`, `erbium_mtimer.h`, `erbium_plic.h`, `erbium_sysreg.h`).

## Interface
- `[erbium_memorymap.h:ERBIUM_SYSREG_BASE]`
- `[erbium_memorymap.h:ERBIUM_UART0_BASE]`
- `[erbium_memorymap.h:ERBIUM_MTIMECMP_BASE]`
- `[erbium_memorymap.h:ERBIUM_MTIME_BASE]`
- `[erbium_memorymap.h:ERBIUM_PLIC_BASE]`
- `[erbium_mtimer.h:ERBIUM_MTIMER_FREQ]`
- `[erbium_mtimer.h:ERBIUM_MTIMER_MTIME]`
- `[erbium_mtimer.h:ERBIUM_MTIMER_MTIMECMP]`
- `[erbium_plic.h:ERBIUM_PLIC_NSOURCE]`
- `[erbium_plic.h:ERBIUM_PLIC_NDEV]`
- `[erbium_plic.h:ERBIUM_PLIC_PRIORITY]`
- `[erbium_plic.h:ERBIUM_PLIC_PENDING]`
- `[erbium_plic.h:ERBIUM_PLIC_ENABLE1]`
- `[erbium_plic.h:ERBIUM_PLIC_THRESHOLD]`
- `[erbium_plic.h:ERBIUM_PLIC_CLAIM]`
- `[erbium_sysreg.h:ERBIUM_SYSREG_SYSTEM_CONFIG]`
- `[erbium_sysreg.h:ERBIUM_SYSREG_UART_ENABLE]`
- `[erbium_uart.h:ERBIUM_UART_BAUD_OFFSET]`
- `[erbium_uart.h:ERBIUM_UART_TX_OFFSET]`
- `[erbium_uart.h:ERBIUM_UART_RX_OFFSET]`
- `[erbium_uart.h:ERBIUM_UART_STATUS_OFFSET]`
- `[erbium_uart.h:ERBIUM_UART_CONTROL_OFFSET]`
- `[erbium_uart.h:ERBIUM_UART_IEN_OFFSET]`
- `[erbium_uart.h:ERBIUM_UART_RX_THRESHOLD_OFFSET]`
- `[erbium_uart.h:ERBIUM_UART_STATUS_TX_EMPTY]`
- `[erbium_uart.h:ERBIUM_UART_STATUS_TX_FULL]`
- `[erbium_uart.h:ERBIUM_UART_STATUS_RX_NOT_EMPTY]`
- `[erbium_uart.h:ERBIUM_UART_IEN_TX_EMPTY]`
- `[erbium_uart.h:ERBIUM_UART_IEN_RX_NOT_EMPTY]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
