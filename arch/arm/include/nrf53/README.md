# nrf53 (`nuttx/arch/arm/include/nrf53`)

## Overview
Hardware abstraction and architecture package for `nrf53` under `nuttx/arch/arm/include/nrf53`, providing 5 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`, `nrf5340_irq.h`, `nrf5340_irq_cpuapp.h`).

## Interface
- `[chip.h:NVIC_SYSH_PRIORITY_MIN]`
- `[chip.h:NVIC_SYSH_PRIORITY_DEFAULT]`
- `[chip.h:NVIC_SYSH_PRIORITY_MAX]`
- `[chip.h:NVIC_SYSH_PRIORITY_STEP]`
- `[irq.h:NRF53_IRQ_RESERVED]`
- `[irq.h:NRF53_IRQ_NMI]`
- `[irq.h:NRF53_IRQ_HARDFAULT]`
- `[irq.h:NRF53_IRQ_MEMFAULT]`
- `[irq.h:NRF53_IRQ_BUSFAULT]`
- `[irq.h:NRF53_IRQ_USAGEFAULT]`
- `[irq.h:NRF53_IRQ_SVCALL]`
- `[irq.h:NRF53_IRQ_DBGMONITOR]`
- `[irq.h:NRF53_IRQ_PENDSV]`
- `[irq.h:NRF53_IRQ_SYSTICK]`
- `[irq.h:NRF53_IRQ_EXTINT]`
- `[nrf5340_irq_cpuapp.h:NRF53_IRQ_FPU]`
- `[nrf5340_irq_cpuapp.h:NRF53_IRQ_CACHE]`
- `[nrf5340_irq_cpuapp.h:NRF53_IRQ_SPU]`
- `[nrf5340_irq_cpuapp.h:NRF53_IRQ_POWER_CLOCK]`
- `[nrf5340_irq_cpuapp.h:NRF53_IRQ_SERIAL0]`
- `[nrf5340_irq_cpuapp.h:NRF53_IRQ_SERIAL1]`
- `[nrf5340_irq_cpuapp.h:NRF53_IRQ_SPIM4]`
- `[nrf5340_irq_cpuapp.h:NRF53_IRQ_SERIAL2]`
- `[nrf5340_irq_cpuapp.h:NRF53_IRQ_SERIAL3]`
- `[nrf5340_irq_cpuapp.h:NRF53_IRQ_GPIOTE0]`
- `[nrf5340_irq_cpuapp.h:NRF53_IRQ_SAADC]`
- `[nrf5340_irq_cpuapp.h:NRF53_IRQ_TIMER0]`
- `[nrf5340_irq_cpunet.h:NRF53_IRQ_POWER_CLOCK]`
- `[nrf5340_irq_cpunet.h:NRF53_IRQ_RADIO]`
- `[nrf5340_irq_cpunet.h:NRF53_IRQ_RNG]`

## Invariants
- `[irq.h:#error]` Compile-time guard: Unsupported NRF53XX MCU
- `[nrf5340_irq.h:#error]` Compile-time guard: Unsupported NRF5340 CPU

## Side Effects
- None

## Verification
- Run: `make test`
