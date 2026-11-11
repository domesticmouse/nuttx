# hardware (`nuttx/arch/risc-v/src/c906/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/risc-v/src/c906/hardware`, providing 5 header file(s) and 0 source file(s) (including `c906_clint.h`, `c906_memorymap.h`, `c906_plic.h`, `c906_sysctl.h`).

## Interface
- `[c906_clint.h:C906_CLINT_MSIP]`
- `[c906_clint.h:C906_CLINT_MTIMECMP]`
- `[c906_clint.h:C906_CLINT_MTIME]`
- `[c906_memorymap.h:C906_PLIC_BASE]`
- `[c906_memorymap.h:C906_CLINT_BASE]`
- `[c906_memorymap.h:C906_CORET_BASE]`
- `[c906_memorymap.h:C906_UART0_BASE]`
- `[c906_plic.h:C906_PLIC_PRIORITY]`
- `[c906_plic.h:C906_PLIC_IP0]`
- `[c906_plic.h:C906_PLIC_IP1]`
- `[c906_plic.h:C906_PLIC_MIE0]`
- `[c906_plic.h:C906_PLIC_MIE1]`
- `[c906_plic.h:C906_PLIC_SIE0]`
- `[c906_plic.h:C906_PLIC_SIE1]`
- `[c906_plic.h:C906_PLIC_CTRL]`
- `[c906_plic.h:C906_PLIC_MTHRESHOLD]`
- `[c906_plic.h:C906_PLIC_MCLAIM]`
- `[c906_plic.h:C906_PLIC_STHRESHOLD]`
- `[c906_plic.h:C906_PLIC_SCLAIM]`
- `[c906_uart.h:ARCH_RISCV_SRC_C906_CHIP_C906_UART_H]`
- `[c906_uart.h:UART_TXDATA_OFFSET]`
- `[c906_uart.h:UART_RXDATA_OFFSET]`
- `[c906_uart.h:UART_TXCTL_OFFSET]`
- `[c906_uart.h:UART_RXCTL_OFFSET]`
- `[c906_uart.h:UART_IE_OFFSET]`
- `[c906_uart.h:UART_IIR_OFFSET]`
- `[c906_uart.h:UART_DIV_OFFSET]`
- `[c906_uart.h:UART_LSR_OFFSET]`
- `[c906_uart.h:UART_MSR_OFFSET]`
- `[c906_uart.h:UART_USR_OFFSET]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
