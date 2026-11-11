# tiva (`nuttx/arch/arm/include/tiva`)

## Overview
Hardware abstraction and architecture package for `tiva` under `nuttx/arch/arm/include/tiva`, providing 7 header file(s) and 0 source file(s) (including `cc13x0_irq.h`, `cc13x2_cc26x2_irq.h`, `chip.h`, `irq.h`).

## Interface
- `[cc13x0_irq.h:TIVA_IRQ_AON_GPIO_EDGE]`
- `[cc13x0_irq.h:TIVA_IRQ_I2C]`
- `[cc13x0_irq.h:TIVA_IRQ_RFC_CPE_1]`
- `[cc13x0_irq.h:TIVA_IRQ_AON_RTC]`
- `[cc13x0_irq.h:TIVA_IRQ_UART0]`
- `[cc13x0_irq.h:TIVA_IRQ_AUX_SWEV0]`
- `[cc13x0_irq.h:TIVA_IRQ_SSI0]`
- `[cc13x0_irq.h:TIVA_IRQ_SSI1]`
- `[cc13x0_irq.h:TIVA_IRQ_RFC_CPE_0]`
- `[cc13x0_irq.h:TIVA_IRQ_RFC_HW]`
- `[cc13x0_irq.h:TIVA_IRQ_RFC_CMD_ACK]`
- `[cc13x0_irq.h:TIVA_IRQ_I2S]`
- `[cc13x2_cc26x2_irq.h:TIVA_IRQ_AON_GPIO_EDGE]`
- `[cc13x2_cc26x2_irq.h:TIVA_IRQ_I2C]`
- `[cc13x2_cc26x2_irq.h:TIVA_IRQ_RFC_CPE_1]`
- `[cc13x2_cc26x2_irq.h:TIVA_IRQ_PKA]`
- `[cc13x2_cc26x2_irq.h:TIVA_IRQ_AON_RTC]`
- `[cc13x2_cc26x2_irq.h:TIVA_IRQ_UART0]`
- `[cc13x2_cc26x2_irq.h:TIVA_IRQ_AUX_SWEV0]`
- `[cc13x2_cc26x2_irq.h:TIVA_IRQ_SSI0]`
- `[cc13x2_cc26x2_irq.h:TIVA_IRQ_SSI1]`
- `[cc13x2_cc26x2_irq.h:TIVA_IRQ_RFC_CPE_0]`
- `[cc13x2_cc26x2_irq.h:TIVA_IRQ_RFC_HW]`
- `[cc13x2_cc26x2_irq.h:TIVA_IRQ_RFC_CMD_ACK]`
- `[chip.h:LM3S]`
- `[chip.h:TIVA_NTIMERS]`
- `[chip.h:TIVA_NWIDETIMERS]`
- `[chip.h:TIVA_NWDT]`
- `[chip.h:TIVA_NETHCONTROLLERS]`
- `[chip.h:TIVA_NLCD]`

## Invariants
- `[chip.h:#error]` Compile-time guard: Capabilities not specified for this TIVA/Stellaris chip
- `[irq.h:#error]` Compile-time guard: Unsupported Stellaris IRQ file
- `[lm3s_irq.h:#error]` Compile-time guard: IRQ Numbers not specified for this Stellaris chip
- `[lm4f_irq.h:#error]` Compile-time guard: IRQ Numbers not known for this Tiva chip
- `[tm4c_irq.h:#error]` Compile-time guard: IRQ Numbers not known for this Tiva chip

## Side Effects
- None

## Verification
- Run: `make test`
