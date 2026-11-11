# iodefs (`nuttx/arch/avr/src/avrdx/iodefs`)

## Overview
Hardware abstraction and architecture package for `iodefs` under `nuttx/arch/avr/src/avrdx/iodefs`, providing 3 header file(s) and 0 source file(s) (including `avr128da28.h`, `avr128da64.h`, `avr128db64.h`).

## Interface
- `[avr128da28.h:avr_usart_t]`
- `[avr128da28.h:avr_twi_t]`
- `[avr128da28.h:PORTMUX_USART0_DEFAULT_GC]`
- `[avr128da28.h:PORTMUX_USART0_ALT1_GC]`
- `[avr128da28.h:PORTMUX_USART0_NONE_GC]`
- `[avr128da28.h:PORTMUX_USART0_GM]`
- `[avr128da28.h:PORTMUX_USART1_DEFAULT_GC]`
- `[avr128da28.h:PORTMUX_USART1_NONE_GC]`
- `[avr128da28.h:PORTMUX_USART1_GM]`
- `[avr128da28.h:PORTMUX_USART2_DEFAULT_GC]`
- `[avr128da28.h:PORTMUX_USART2_NONE_GC]`
- `[avr128da28.h:PORTMUX_USART2_GM]`
- `[avr128da28.h:PORTMUX_TWI0_DEFAULT_GC]`
- `[avr128da28.h:PORTMUX_TWI0_ALT2_GC]`
- `[avr128da64.h:avr_usart_t]`
- `[avr128da64.h:avr_twi_t]`
- `[avr128da64.h:PORTMUX_USART0_DEFAULT_GC]`
- `[avr128da64.h:PORTMUX_USART0_ALT1_GC]`
- `[avr128da64.h:PORTMUX_USART0_NONE_GC]`
- `[avr128da64.h:PORTMUX_USART0_GM]`
- `[avr128da64.h:PORTMUX_USART1_DEFAULT_GC]`
- `[avr128da64.h:PORTMUX_USART1_ALT1_GC]`
- `[avr128da64.h:PORTMUX_USART1_NONE_GC]`
- `[avr128da64.h:PORTMUX_USART1_GM]`
- `[avr128da64.h:PORTMUX_USART2_DEFAULT_GC]`
- `[avr128da64.h:PORTMUX_USART2_ALT1_gc]`
- `[avr128da64.h:PORTMUX_USART2_NONE_GC]`
- `[avr128da64.h:PORTMUX_USART2_GM]`
- `[avr128db64.h:avr_usart_t]`
- `[avr128db64.h:avr_twi_t]`

## Invariants
- `[avr128da28.h:#error]` Compile-time guard: Do not include this file directly, use avrdx_iodefs.h instead
- `[avr128da64.h:#error]` Compile-time guard: Do not include this file directly, use avrdx_iodefs.h instead
- `[avr128db64.h:#error]` Compile-time guard: Do not include this file directly, use avrdx_iodefs.h instead

## Side Effects
- None

## Verification
- Run: `make test`
