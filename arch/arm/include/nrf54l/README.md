# nrf54l (`nuttx/arch/arm/include/nrf54l`)

## Overview
Hardware abstraction and architecture package for `nrf54l` under `nuttx/arch/arm/include/nrf54l`, providing 3 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`, `nrf54l_irq.h`).

## Interface
- `[chip.h:NVIC_SYSH_PRIORITY_MIN]`
- `[chip.h:NVIC_SYSH_PRIORITY_DEFAULT]`
- `[chip.h:NVIC_SYSH_PRIORITY_MAX]`
- `[chip.h:NVIC_SYSH_PRIORITY_STEP]`
- `[irq.h:NRF54L_IRQ_RESERVED]`
- `[irq.h:NRF54L_IRQ_NMI]`
- `[irq.h:NRF54L_IRQ_HARDFAULT]`
- `[irq.h:NRF54L_IRQ_MEMFAULT]`
- `[irq.h:NRF54L_IRQ_BUSFAULT]`
- `[irq.h:NRF54L_IRQ_USAGEFAULT]`
- `[irq.h:NRF54L_IRQ_SECUREFAULT]`
- `[irq.h:NRF54L_IRQ_SVCALL]`
- `[irq.h:NRF54L_IRQ_DBGMONITOR]`
- `[irq.h:NRF54L_IRQ_PENDSV]`
- `[irq.h:NRF54L_IRQ_SYSTICK]`
- `[irq.h:NRF54L_IRQ_EXTINT]`
- `[nrf54l_irq.h:NRF54L_IRQ_SWI00]`
- `[nrf54l_irq.h:NRF54L_IRQ_SWI01]`
- `[nrf54l_irq.h:NRF54L_IRQ_SWI02]`
- `[nrf54l_irq.h:NRF54L_IRQ_SWI03]`
- `[nrf54l_irq.h:NRF54L_IRQ_SPU00]`
- `[nrf54l_irq.h:NRF54L_IRQ_MPC00]`
- `[nrf54l_irq.h:NRF54L_IRQ_VPR00]`
- `[nrf54l_irq.h:NRF54L_IRQ_CTRLAP]`
- `[nrf54l_irq.h:NRF54L_IRQ_CM33SS]`
- `[nrf54l_irq.h:NRF54L_IRQ_TIMER00]`
- `[nrf54l_irq.h:NRF54L_IRQ_AXONS]`
- `[nrf54l_irq.h:NRF54L_IRQ_EGU00]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
