# hardware (`nuttx/arch/risc-v/src/rv32m1/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/risc-v/src/rv32m1/hardware`, providing 16 header file(s) and 0 source file(s) (including `rv32m1_eu.h`, `rv32m1_gpio.h`, `rv32m1_intmux.h`, `rv32m1_lpit.h`).

## Interface
- `[rv32m1_eu.h:RV32M1_EU_INTPTEN_OFFSET]`
- `[rv32m1_eu.h:RV32M1_EU_INTPTPEND_OFFSET]`
- `[rv32m1_eu.h:RV32M1_EU_INTPTPENDSET_OFFSET]`
- `[rv32m1_eu.h:RV32M1_EU_INTPTPENDCLR_OFFSET]`
- `[rv32m1_eu.h:RV32M1_EU_INTPTSECURE_OFFSET]`
- `[rv32m1_eu.h:RV32M1_EU_INTPTPRI0_OFFSET]`
- `[rv32m1_eu.h:RV32M1_EU_INTPTPRI1_OFFSET]`
- `[rv32m1_eu.h:RV32M1_EU_INTPTPRI2_OFFSET]`
- `[rv32m1_eu.h:RV32M1_EU_INTPTPRI3_OFFSET]`
- `[rv32m1_eu.h:RV32M1_EU_INTPTBASE_OFFSET]`
- `[rv32m1_eu.h:RV32M1_EU_INTPTENACTIVE_OFFSET]`
- `[rv32m1_eu.h:RV32M1_EU_INTACTPRI0_OFFSET]`
- `[rv32m1_gpio.h:RV32M1_GPIO_PDOR_OFFSET]`
- `[rv32m1_gpio.h:RV32M1_GPIO_PSOR_OFFSET]`
- `[rv32m1_gpio.h:RV32M1_GPIO_PCOR_OFFSET]`
- `[rv32m1_gpio.h:RV32M1_GPIO_PTOR_OFFSET]`
- `[rv32m1_gpio.h:RV32M1_GPIO_PDIR_OFFSET]`
- `[rv32m1_gpio.h:RV32M1_GPIO_PDDR_OFFSET]`
- `[rv32m1_intmux.h:RV32M1_INTMUX_CH0_CSR_OFFSET]`
- `[rv32m1_intmux.h:RV32M1_INTMUX_CH0_VEC_OFFSET]`
- `[rv32m1_intmux.h:RV32M1_INTMUX_CH0_IER_OFFSET]`
- `[rv32m1_intmux.h:RV32M1_INTMUX_CH0_IPR_OFFSET]`
- `[rv32m1_intmux.h:RV32M1_INTMUX_CH1_CSR_OFFSET]`
- `[rv32m1_intmux.h:RV32M1_INTMUX_CH1_VEC_OFFSET]`
- `[rv32m1_intmux.h:RV32M1_INTMUX_CH1_IER_OFFSET]`
- `[rv32m1_intmux.h:RV32M1_INTMUX_CH1_IPR_OFFSET]`
- `[rv32m1_intmux.h:RV32M1_INTMUX_CH2_CSR_OFFSET]`
- `[rv32m1_intmux.h:RV32M1_INTMUX_CH2_VEC_OFFSET]`
- `[rv32m1_intmux.h:RV32M1_INTMUX_CH2_IER_OFFSET]`
- `[rv32m1_intmux.h:RV32M1_INTMUX_CH2_IPR_OFFSET]`

## Invariants
- `[rv32m1_memorymap.h:#error]` Compile-time guard: rv32m1 zero-riscy is to be continued...
- `[rv32m1_scg.h:#error]` Compile-time guard: rv32m1 zero-riscy is to be continued...
- `[rv32m1_wdog.h:#error]` Compile-time guard: Unsupported RV32M1 Watch dog

## Side Effects
- None

## Verification
- Run: `make test`
