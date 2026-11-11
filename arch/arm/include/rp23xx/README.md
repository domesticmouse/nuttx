# rp23xx (`nuttx/arch/arm/include/rp23xx`)

## Overview
Hardware abstraction and architecture package for `rp23xx` under `nuttx/arch/arm/include/rp23xx`, providing 5 header file(s) and 0 source file(s) (including `chip.h`, `i2c_slave.h`, `irq.h`, `pm.h`).

## Interface
- `[chip.h:NVIC_SYSH_PRIORITY_MIN]`
- `[chip.h:NVIC_SYSH_PRIORITY_DEFAULT]`
- `[chip.h:NVIC_SYSH_PRIORITY_MAX]`
- `[chip.h:NVIC_SYSH_PRIORITY_STEP]`
- `[chip.h:ARMV8M_PERIPHERAL_INTERRUPTS]`
- `[i2c_slave.h:rp23xx_i2c0_slave_initialize]`
- `[i2c_slave.h:rp23xx_i2c1_slave_initialize]`
- `[irq.h:RP23XX_IRQ_RESERVED]`
- `[irq.h:RP23XX_IRQ_NMI]`
- `[irq.h:RP23XX_IRQ_HARDFAULT]`
- `[irq.h:RP23XX_IRQ_SVCALL]`
- `[irq.h:RP23XX_IRQ_PENDSV]`
- `[irq.h:RP23XX_IRQ_SYSTICK]`
- `[irq.h:RP23XX_IRQ_EXTINT]`
- `[irq.h:RP23XX_TIMER0_IRQ_0]`
- `[irq.h:RP23XX_TIMER0_IRQ_1]`
- `[irq.h:RP23XX_TIMER0_IRQ_2]`
- `[irq.h:RP23XX_TIMER0_IRQ_3]`
- `[irq.h:RP23XX_TIMER1_IRQ_0]`
- `[pm.h:rp23xx_suspend_s]`
- `[pm.h:BOARDIOC_RP23XX_SUSPEND]`
- `[watchdog.h:WDIOC_SET_SCRATCH0]`
- `[watchdog.h:WDIOC_SET_SCRATCH1]`
- `[watchdog.h:WDIOC_SET_SCRATCH2]`
- `[watchdog.h:WDIOC_SET_SCRATCH3]`
- `[watchdog.h:WDIOC_SET_SCRATCH4]`
- `[watchdog.h:WDIOC_SET_SCRATCH5]`
- `[watchdog.h:WDIOC_SET_SCRATCH6]`
- `[watchdog.h:WDIOC_SET_SCRATCH7]`
- `[watchdog.h:WDIOC_SET_SCRATCH]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
