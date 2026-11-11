# nrf52 (`nuttx/arch/arm/include/nrf52`)

## Overview
Hardware abstraction and architecture package for `nrf52` under `nuttx/arch/arm/include/nrf52`, providing 3 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`, `nrf52_irq.h`).

## Interface
- `[chip.h:NVIC_SYSH_PRIORITY_MIN]`
- `[chip.h:NVIC_SYSH_PRIORITY_DEFAULT]`
- `[chip.h:NVIC_SYSH_PRIORITY_MAX]`
- `[chip.h:NVIC_SYSH_PRIORITY_STEP]`
- `[irq.h:NRF52_IRQ_RESERVED]`
- `[irq.h:NRF52_IRQ_NMI]`
- `[irq.h:NRF52_IRQ_HARDFAULT]`
- `[irq.h:NRF52_IRQ_MEMFAULT]`
- `[irq.h:NRF52_IRQ_BUSFAULT]`
- `[irq.h:NRF52_IRQ_USAGEFAULT]`
- `[irq.h:NRF52_IRQ_SIGNVALUE]`
- `[irq.h:NRF52_IRQ_SVCALL]`
- `[irq.h:NRF52_IRQ_DBGMONITOR]`
- `[irq.h:NRF52_IRQ_PENDSV]`
- `[irq.h:NRF52_IRQ_SYSTICK]`
- `[irq.h:NRF52_IRQ_EXTINT]`
- `[nrf52_irq.h:NRF52_IRQ_POWER_CLOCK]`
- `[nrf52_irq.h:NRF52_IRQ_RADIO]`
- `[nrf52_irq.h:NRF52_IRQ_UART0]`
- `[nrf52_irq.h:NRF52_IRQ_SPI_TWI_0]`
- `[nrf52_irq.h:NRF52_IRQ_SPI_TWI_1]`
- `[nrf52_irq.h:NRF52_IRQ_NFCT]`
- `[nrf52_irq.h:NRF52_IRQ_GPIOTE]`
- `[nrf52_irq.h:NRF52_IRQ_SAADC]`
- `[nrf52_irq.h:NRF52_IRQ_TIMER0]`
- `[nrf52_irq.h:NRF52_IRQ_TIMER1]`
- `[nrf52_irq.h:NRF52_IRQ_TIMER2]`
- `[nrf52_irq.h:NRF52_IRQ_RTC0]`

## Invariants
- `[irq.h:#error]` Compile-time guard: Unsupported NRF52XX MCU
- `[nrf52_irq.h:#error]` Compile-time guard: Unknown NRF52 chip !

## Side Effects
- None

## Verification
- Run: `make test`
