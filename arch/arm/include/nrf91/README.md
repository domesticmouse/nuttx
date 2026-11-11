# nrf91 (`nuttx/arch/arm/include/nrf91`)

## Overview
Hardware abstraction and architecture package for `nrf91` under `nuttx/arch/arm/include/nrf91`, providing 3 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`, `nrf9160_irq.h`).

## Interface
- `[chip.h:NVIC_SYSH_PRIORITY_MIN]`
- `[chip.h:NVIC_SYSH_PRIORITY_DEFAULT]`
- `[chip.h:NVIC_SYSH_PRIORITY_MAX]`
- `[chip.h:NVIC_SYSH_PRIORITY_STEP]`
- `[irq.h:NRF91_IRQ_RESERVED]`
- `[irq.h:NRF91_IRQ_NMI]`
- `[irq.h:NRF91_IRQ_HARDFAULT]`
- `[irq.h:NRF91_IRQ_MEMFAULT]`
- `[irq.h:NRF91_IRQ_BUSFAULT]`
- `[irq.h:NRF91_IRQ_USAGEFAULT]`
- `[irq.h:NRF91_IRQ_SVCALL]`
- `[irq.h:NRF91_IRQ_DBGMONITOR]`
- `[irq.h:NRF91_IRQ_PENDSV]`
- `[irq.h:NRF91_IRQ_SYSTICK]`
- `[irq.h:NRF91_IRQ_EXTINT]`
- `[nrf9160_irq.h:NRF91_IRQ_SPU]`
- `[nrf9160_irq.h:NRF91_IRQ_REGULATORS]`
- `[nrf9160_irq.h:NRF91_IRQ_POWER_CLOCK]`
- `[nrf9160_irq.h:NRF91_IRQ_SERIAL0]`
- `[nrf9160_irq.h:NRF91_IRQ_SERIAL1]`
- `[nrf9160_irq.h:NRF91_IRQ_SERIAL2]`
- `[nrf9160_irq.h:NRF91_IRQ_SERIAL3]`
- `[nrf9160_irq.h:NRF91_IRQ_GPIOTE0]`
- `[nrf9160_irq.h:NRF91_IRQ_SAADC]`
- `[nrf9160_irq.h:NRF91_IRQ_TIMER0]`
- `[nrf9160_irq.h:NRF91_IRQ_TIMER1]`
- `[nrf9160_irq.h:NRF91_IRQ_TIMER2]`

## Invariants
- `[irq.h:#error]` Compile-time guard: Unsupported NRF91XX MCU

## Side Effects
- None

## Verification
- Run: `make test`
