# hardware (`nuttx/arch/arm64/src/am62x/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm64/src/am62x/hardware`, providing 6 header file(s) and 0 source file(s) (including `am62x_gpio.h`, `am62x_i2c.h`, `am62x_memorymap.h`, `am62x_secure_proxy.h`).

## Interface
- `[am62x_gpio.h:AM62X_GPIO_NBANKS]`
- `[am62x_gpio.h:AM62X_GPIO_NPINS]`
- `[am62x_gpio.h:AM62X_GPIO_BINTEN_OFFSET]`
- `[am62x_gpio.h:AM62X_GPIO_BANK_STRIDE]`
- `[am62x_gpio.h:AM62X_GPIO_BANK_OFFSET]`
- `[am62x_gpio.h:AM62X_GPIO_DIR_OFFSET]`
- `[am62x_gpio.h:AM62X_GPIO_OUT_DATA_OFFSET]`
- `[am62x_gpio.h:AM62X_GPIO_SET_DATA_OFFSET]`
- `[am62x_gpio.h:AM62X_GPIO_CLR_DATA_OFFSET]`
- `[am62x_gpio.h:AM62X_GPIO_IN_DATA_OFFSET]`
- `[am62x_gpio.h:AM62X_GPIO_SET_RIS_TRIG_OFFSET]`
- `[am62x_gpio.h:AM62X_GPIO_CLR_RIS_TRIG_OFFSET]`
- `[am62x_i2c.h:AM62X_I2C_REVNB_LO_OFFSET]`
- `[am62x_i2c.h:AM62X_I2C_REVNB_HI_OFFSET]`
- `[am62x_i2c.h:AM62X_I2C_SYSC_OFFSET]`
- `[am62x_i2c.h:AM62X_I2C_IRQSTATUS_RAW_OFFSET]`
- `[am62x_i2c.h:AM62X_I2C_IRQSTATUS_OFFSET]`
- `[am62x_i2c.h:AM62X_I2C_IRQENABLE_SET_OFFSET]`
- `[am62x_i2c.h:AM62X_I2C_IRQENABLE_CLR_OFFSET]`
- `[am62x_i2c.h:AM62X_I2C_WE_OFFSET]`
- `[am62x_i2c.h:AM62X_I2C_SYSS_OFFSET]`
- `[am62x_i2c.h:AM62X_I2C_BUF_OFFSET]`
- `[am62x_i2c.h:AM62X_I2C_CNT_OFFSET]`
- `[am62x_i2c.h:AM62X_I2C_DATA_OFFSET]`
- `[am62x_memorymap.h:AM62X_UART0_BASE]`
- `[am62x_memorymap.h:AM62X_UART1_BASE]`
- `[am62x_memorymap.h:AM62X_UART2_BASE]`
- `[am62x_memorymap.h:AM62X_UART3_BASE]`
- `[am62x_memorymap.h:AM62X_UART4_BASE]`
- `[am62x_memorymap.h:AM62X_UART5_BASE]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
