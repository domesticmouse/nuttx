# hardware (`nuttx/arch/arm/src/cxd32xx/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/cxd32xx/hardware`, providing 4 header file(s) and 0 source file(s) (including `cxd3277_clockfreq.h`, `cxd3277_memorymap.h`, `cxd32_timer.h`, `cxd32_uart.h`).

## Interface
- `[cxd3277_clockfreq.h:CXD32_TIMER_BASEFREQ]`
- `[cxd3277_clockfreq.h:CXD32_UART_BASEFREQ]`
- `[cxd3277_memorymap.h:CXD32_UART0_BASE]`
- `[cxd3277_memorymap.h:CXD32_UART1_BASE]`
- `[cxd3277_memorymap.h:CXD32_UART2_BASE]`
- `[cxd3277_memorymap.h:CXD32_TIMER0_BASE]`
- `[cxd3277_memorymap.h:CXD32_TIMER1_BASE]`
- `[cxd3277_memorymap.h:CXD32_TIMER2_BASE]`
- `[cxd3277_memorymap.h:CXD32_TIMER3_BASE]`
- `[cxd3277_memorymap.h:CXD32_TIMER4_BASE]`
- `[cxd3277_memorymap.h:CXD32_INTC_BASE]`
- `[cxd32_timer.h:CXD32_TIMER_LOAD]`
- `[cxd32_timer.h:CXD32_TIMER_VALUE]`
- `[cxd32_timer.h:CXD32_TIMER_CONTROL]`
- `[cxd32_timer.h:CXD32_TIMER_INTCLR]`
- `[cxd32_timer.h:CXD32_TIMER_RIS]`
- `[cxd32_timer.h:CXD32_TIMER_MIS]`
- `[cxd32_timer.h:CXD32_TIMER_BGLOAD]`
- `[cxd32_timer.h:CXD32_TIMER_ITCR]`
- `[cxd32_timer.h:CXD32_TIMER_ITOP]`
- `[cxd32_timer.h:CXD32_TIMER_PERIPHID0]`
- `[cxd32_timer.h:CXD32_TIMER_PERIPHID1]`
- `[cxd32_timer.h:CXD32_TIMER_PERIPHID2]`
- `[cxd32_uart.h:CXD32_UART_DR]`
- `[cxd32_uart.h:CXD32_UART_RSR_ECR]`
- `[cxd32_uart.h:CXD32_UART_FR]`
- `[cxd32_uart.h:CXD32_UART_ILPR]`
- `[cxd32_uart.h:CXD32_UART_IBRD]`
- `[cxd32_uart.h:CXD32_UART_FBRD]`
- `[cxd32_uart.h:CXD32_UART_LCR_H]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
