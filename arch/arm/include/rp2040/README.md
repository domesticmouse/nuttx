# rp2040 (`nuttx/arch/arm/include/rp2040`)

## Overview
Hardware abstraction and architecture package for `rp2040` under `nuttx/arch/arm/include/rp2040`, providing 4 header file(s) and 0 source file(s) (including `chip.h`, `i2c_slave.h`, `irq.h`, `watchdog.h`).

## Interface
- `[chip.h:NVIC_SYSH_PRIORITY_MIN]`
- `[chip.h:NVIC_SYSH_PRIORITY_DEFAULT]`
- `[chip.h:NVIC_SYSH_PRIORITY_MAX]`
- `[chip.h:NVIC_SYSH_PRIORITY_STEP]`
- `[i2c_slave.h:rp2040_i2c0_slave_initialize]`
- `[i2c_slave.h:rp2040_i2c1_slave_initialize]`
- `[irq.h:RP2040_IRQ_RESERVED]`
- `[irq.h:RP2040_IRQ_NMI]`
- `[irq.h:RP2040_IRQ_HARDFAULT]`
- `[irq.h:RP2040_IRQ_SVCALL]`
- `[irq.h:RP2040_IRQ_PENDSV]`
- `[irq.h:RP2040_IRQ_SYSTICK]`
- `[irq.h:RP2040_IRQ_EXTINT]`
- `[irq.h:RP2040_TIMER_IRQ_0]`
- `[irq.h:RP2040_TIMER_IRQ_1]`
- `[irq.h:RP2040_TIMER_IRQ_2]`
- `[irq.h:RP2040_TIMER_IRQ_3]`
- `[irq.h:RP2040_PWM_IRQ_WRAP]`
- `[watchdog.h:WDIOC_SET_SCRATCH0]`
- `[watchdog.h:WDIOC_SET_SCRATCH1]`
- `[watchdog.h:WDIOC_SET_SCRATCH2]`
- `[watchdog.h:WDIOC_SET_SCRATCH3]`
- `[watchdog.h:WDIOC_SET_SCRATCH4]`
- `[watchdog.h:WDIOC_SET_SCRATCH5]`
- `[watchdog.h:WDIOC_SET_SCRATCH6]`
- `[watchdog.h:WDIOC_SET_SCRATCH7]`
- `[watchdog.h:WDIOC_SET_SCRATCH]`
- `[watchdog.h:WDIOC_GET_SCRATCH0]`
- `[watchdog.h:WDIOC_GET_SCRATCH1]`
- `[watchdog.h:WDIOC_GET_SCRATCH2]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
