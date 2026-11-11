# hardware (`nuttx/arch/risc-v/src/bl808/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/risc-v/src/bl808/hardware`, providing 10 header file(s) and 0 source file(s) (including `bl808_glb.h`, `bl808_gpadc.h`, `bl808_i2c.h`, `bl808_m0ic.h`).

## Interface
- `[bl808_glb.h:BL808_GLB_UART_CFG1_OFFSET]`
- `[bl808_glb.h:BL808_GLB_UART_CFG2_OFFSET]`
- `[bl808_glb.h:BL808_GLB_I2C_CFG0_OFFSET]`
- `[bl808_glb.h:BL808_GLB_SPI_CFG0_OFFSET]`
- `[bl808_glb.h:BL808_GLB_PARM_CFG0_OFFSET]`
- `[bl808_glb.h:BL808_GPIO_CFG_OFFSET]`
- `[bl808_glb.h:BL808_GLB_UART_CFG1]`
- `[bl808_glb.h:BL808_GLB_UART_CFG2]`
- `[bl808_glb.h:BL808_GLB_I2C_CFG0]`
- `[bl808_glb.h:BL808_GLB_SPI_CFG0]`
- `[bl808_glb.h:BL808_GLB_PARM_CFG0]`
- `[bl808_glb.h:BL808_GPIO_CFG]`
- `[bl808_gpadc.h:BL808_GPADC_CONFIG_OFFSET]`
- `[bl808_gpadc.h:BL808_GPADC_DMA_RDATA_OFFSET]`
- `[bl808_gpadc.h:BL808_GPADC_PIR_TRAIN_OFFSET]`
- `[bl808_gpadc.h:BL808_GPADC_CMD_OFFSET]`
- `[bl808_gpadc.h:BL808_GPADC_CONFIG1_OFFSET]`
- `[bl808_gpadc.h:BL808_GPADC_CONFIG2_OFFSET]`
- `[bl808_gpadc.h:BL808_GPADC_SCAN_POS1_OFFSET]`
- `[bl808_gpadc.h:BL808_GPADC_SCAN_POS2_OFFSET]`
- `[bl808_gpadc.h:BL808_GPADC_SCAN_NEG1_OFFSET]`
- `[bl808_gpadc.h:BL808_GPADC_SCAN_NEG2_OFFSET]`
- `[bl808_gpadc.h:BL808_GPADC_STATUS_OFFSET]`
- `[bl808_gpadc.h:BL808_GPADC_ISR_OFFSET]`
- `[bl808_i2c.h:BL808_I2C_BASE]`
- `[bl808_i2c.h:BL808_I2C_CONFIG_OFFSET]`
- `[bl808_i2c.h:BL808_I2C_INT_STS_OFFSET]`
- `[bl808_i2c.h:BL808_I2C_SUB_ADDR_OFFSET]`
- `[bl808_i2c.h:BL808_I2C_BUSY_OFFSET]`
- `[bl808_i2c.h:BL808_I2C_PRD_START_OFFSET]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
