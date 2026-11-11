# tm4c (`nuttx/arch/arm/src/tiva/hardware/tm4c`)

## Overview
Hardware abstraction and architecture package for `tm4c` under `nuttx/arch/arm/src/tiva/hardware/tm4c`, providing 13 header file(s) and 0 source file(s) (including `tm4c123_gpio.h`, `tm4c123_i2c.h`, `tm4c123_sysctrl.h`, `tm4c123_timer.h`).

## Interface
- `[tm4c123_gpio.h:TIVA_GPIOK_BASE]`
- `[tm4c123_gpio.h:TIVA_GPIOL_BASE]`
- `[tm4c123_gpio.h:TIVA_GPIOM_BASE]`
- `[tm4c123_gpio.h:TIVA_GPION_BASE]`
- `[tm4c123_gpio.h:TIVA_GPIOP_BASE]`
- `[tm4c123_gpio.h:TIVA_GPIOQ_BASE]`
- `[tm4c123_gpio.h:TIVA_GPIOR_BASE]`
- `[tm4c123_gpio.h:TIVA_GPIOS_BASE]`
- `[tm4c123_gpio.h:TIVA_GPIOT_BASE]`
- `[tm4c123_gpio.h:TIVA_GPIO_DATA_OFFSET]`
- `[tm4c123_gpio.h:TIVA_GPIO_DIR_OFFSET]`
- `[tm4c123_gpio.h:TIVA_GPIO_IS_OFFSET]`
- `[tm4c123_i2c.h:TIVA_I2CM_SA_OFFSET]`
- `[tm4c123_i2c.h:TIVA_I2CM_CS_OFFSET]`
- `[tm4c123_i2c.h:TIVA_I2CM_DR_OFFSET]`
- `[tm4c123_i2c.h:TIVA_I2CM_TPR_OFFSET]`
- `[tm4c123_i2c.h:TIVA_I2CM_IMR_OFFSET]`
- `[tm4c123_i2c.h:TIVA_I2CM_RIS_OFFSET]`
- `[tm4c123_i2c.h:TIVA_I2CM_MIS_OFFSET]`
- `[tm4c123_i2c.h:TIVA_I2CM_ICR_OFFSET]`
- `[tm4c123_i2c.h:TIVA_I2CM_CR_OFFSET]`
- `[tm4c123_i2c.h:TIVA_I2CM_CLKOCNT_OFFSET]`
- `[tm4c123_i2c.h:TIVA_I2CM_BMON_OFFSET]`
- `[tm4c123_i2c.h:TIVA_I2CM_CR2_OFFSET]`
- `[tm4c123_sysctrl.h:TIVA_SYSCON_DID0_OFFSET]`
- `[tm4c123_sysctrl.h:TIVA_SYSCON_DID1_OFFSET]`
- `[tm4c123_sysctrl.h:TIVA_SYSCON_PBORCTL_OFFSET]`
- `[tm4c123_sysctrl.h:TIVA_SYSCON_RIS_OFFSET]`
- `[tm4c123_sysctrl.h:TIVA_SYSCON_IMC_OFFSET]`
- `[tm4c123_sysctrl.h:TIVA_SYSCON_MISC_OFFSET]`

## Invariants
- `[tm4c_memorymap.h:#error]` Compile-time guard: Memory map not specified for this TM4C chip
- `[tm4c_pinmap.h:#error]` Compile-time guard: Unknown TIVA chip

## Side Effects
- None

## Verification
- Run: `make test`
