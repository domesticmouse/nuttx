# rp23xx-rv (`nuttx/arch/risc-v/include/rp23xx-rv`)

## Overview
Hardware abstraction and architecture package for `rp23xx-rv` under `nuttx/arch/risc-v/include/rp23xx-rv`, providing 4 header file(s) and 0 source file(s) (including `chip.h`, `i2c_slave.h`, `irq.h`, `watchdog.h`).

## Interface
- `[i2c_slave.h:rp23xx_i2c0_slave_initialize]`
- `[i2c_slave.h:rp23xx_i2c1_slave_initialize]`
- `[irq.h:RP23XX_IRQ_EXTINT]`
- `[irq.h:RP23XX_TIMER0_IRQ_0]`
- `[irq.h:RP23XX_TIMER0_IRQ_1]`
- `[irq.h:RP23XX_TIMER0_IRQ_2]`
- `[irq.h:RP23XX_TIMER0_IRQ_3]`
- `[irq.h:RP23XX_TIMER1_IRQ_0]`
- `[irq.h:RP23XX_TIMER1_IRQ_1]`
- `[irq.h:RP23XX_TIMER1_IRQ_2]`
- `[irq.h:RP23XX_TIMER1_IRQ_3]`
- `[irq.h:RP23XX_RV_PWM_IRQ_WRAP_0]`
- `[irq.h:RP23XX_RV_PWM_IRQ_WRAP_1]`
- `[irq.h:RP23XX_DMA_IRQ_0]`
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
