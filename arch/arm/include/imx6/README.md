# imx6 (`nuttx/arch/arm/include/imx6`)

## Overview
Hardware abstraction and architecture package for `imx6` under `nuttx/arch/arm/include/imx6`, providing 2 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`).

## Interface
- `[chip.h:IMX_OCRAM_SIZE]`
- `[chip.h:IMX_L2CACHE_SIZE]`
- `[chip.h:IMX_NXCPUS]`
- `[chip.h:IMX_NGPU3D]`
- `[chip.h:IMX_N32SHADERS]`
- `[chip.h:IMX_NGPU2D]`
- `[chip.h:IMX_HAVE_DDR64]`
- `[chip.h:IMX_HAVE_DDR32x2]`
- `[chip.h:IMX_HAVE_SATAII]`
- `[irq.h:IMX_IRQ_SGI0]`
- `[irq.h:IMX_IRQ_SGI1]`
- `[irq.h:IMX_IRQ_SGI2]`
- `[irq.h:IMX_IRQ_SGI3]`
- `[irq.h:IMX_IRQ_SGI4]`
- `[irq.h:IMX_IRQ_SGI5]`
- `[irq.h:IMX_IRQ_SGI6]`
- `[irq.h:IMX_IRQ_SGI7]`
- `[irq.h:IMX_IRQ_SGI8]`
- `[irq.h:IMX_IRQ_SGI9]`
- `[irq.h:IMX_IRQ_SGI10]`
- `[irq.h:IMX_IRQ_SGI11]`

## Invariants
- `[chip.h:#error]` Compile-time guard: Unspecified i.MX6 chip

## Side Effects
- None

## Verification
- Run: `make test`
