# hardware (`nuttx/arch/arm/src/s32k1xx/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/s32k1xx/hardware`, providing 37 header file(s) and 0 source file(s) (including `s32k116_pinmux.h`, `s32k118_pinmux.h`, `s32k11x_dmamux.h`, `s32k142_pinmux.h`).

## Interface
- `[s32k116_pinmux.h:PIN_ADC0_SE0]`
- `[s32k116_pinmux.h:PIN_ADC0_SE1]`
- `[s32k116_pinmux.h:PIN_ADC0_SE3]`
- `[s32k116_pinmux.h:PIN_ADC0_SE4]`
- `[s32k116_pinmux.h:PIN_ADC0_SE5]`
- `[s32k116_pinmux.h:PIN_ADC0_SE6]`
- `[s32k116_pinmux.h:PIN_ADC0_SE7]`
- `[s32k116_pinmux.h:PIN_ADC0_SE9]`
- `[s32k116_pinmux.h:PIN_ADC0_SE10]`
- `[s32k116_pinmux.h:PIN_ADC0_SE11]`
- `[s32k116_pinmux.h:PIN_ADC0_SE12]`
- `[s32k116_pinmux.h:PIN_ADC0_SE13]`
- `[s32k118_pinmux.h:PIN_ADC0_SE0]`
- `[s32k118_pinmux.h:PIN_ADC0_SE1]`
- `[s32k118_pinmux.h:PIN_ADC0_SE2]`
- `[s32k118_pinmux.h:PIN_ADC0_SE3]`
- `[s32k118_pinmux.h:PIN_ADC0_SE4]`
- `[s32k118_pinmux.h:PIN_ADC0_SE5]`
- `[s32k118_pinmux.h:PIN_ADC0_SE6]`
- `[s32k118_pinmux.h:PIN_ADC0_SE7]`
- `[s32k118_pinmux.h:PIN_ADC0_SE8]`
- `[s32k118_pinmux.h:PIN_ADC0_SE9]`
- `[s32k118_pinmux.h:PIN_ADC0_SE10]`
- `[s32k118_pinmux.h:PIN_ADC0_SE11]`
- `[s32k11x_dmamux.h:S32K1XX_DMACHAN_DISABLED]`
- `[s32k11x_dmamux.h:S32K1XX_DMACHAN_LPUART0_RX]`
- `[s32k11x_dmamux.h:S32K1XX_DMACHAN_LPUART0_TX]`
- `[s32k11x_dmamux.h:S32K1XX_DMACHAN_LPUART1_RX]`
- `[s32k11x_dmamux.h:S32K1XX_DMACHAN_LPUART1_TX]`
- `[s32k11x_dmamux.h:S32K1XX_DMACHAN_FLEXIO_SHIFTER0]`

## Invariants
- `[s32k1xx_edma.h:#error]` Compile-time guard: Unknown number of DMA channels for this S32K1xx part
- `[s32k1xx_pinmux.h:#error]` Compile-time guard: No pin multiplexing for this S32K1xx part

## Side Effects
- None

## Verification
- Run: `make test`
