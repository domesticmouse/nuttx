# hardware (`nuttx/arch/arm/src/sama5/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/sama5/hardware`, providing 60 header file(s) and 0 source file(s) (including `_sama5d2x_memorymap.h`, `_sama5d2x_pinmap.h`, `_sama5d2x_pio.h`, `_sama5d3x4x_pio.h`).

## Interface
- `[_sama5d2x_memorymap.h:__CONCAT]`
- `[_sama5d2x_memorymap.h:MKULONG]`
- `[_sama5d2x_memorymap.h:SAM_INTMEM_PSECTION]`
- `[_sama5d2x_memorymap.h:SAM_EBICS0_PSECTION]`
- `[_sama5d2x_memorymap.h:SAM_DDRCS_PSECTION]`
- `[_sama5d2x_memorymap.h:SAM_DDRAESCS_PSECTION]`
- `[_sama5d2x_memorymap.h:SAM_EBICS1_PSECTION]`
- `[_sama5d2x_memorymap.h:SAM_EBICS2_PSECTION]`
- `[_sama5d2x_memorymap.h:SAM_EBICS3_PSECTION]`
- `[_sama5d2x_memorymap.h:SAM_QSPI0AES_PSECTION]`
- `[_sama5d2x_memorymap.h:SAM_QSPI1AES_PSECTION]`
- `[_sama5d2x_memorymap.h:SAM_SDMMC0_PSECTION]`
- `[_sama5d2x_pinmap.h:PIO_ADC_AD0]`
- `[_sama5d2x_pinmap.h:PIO_ADC_AD1]`
- `[_sama5d2x_pinmap.h:PIO_ADC_AD2]`
- `[_sama5d2x_pinmap.h:PIO_ADC_AD3]`
- `[_sama5d2x_pinmap.h:PIO_ADC_AD4]`
- `[_sama5d2x_pinmap.h:PIO_ADC_AD5]`
- `[_sama5d2x_pinmap.h:PIO_ADC_AD6]`
- `[_sama5d2x_pinmap.h:PIO_ADC_AD7]`
- `[_sama5d2x_pinmap.h:PIO_ADC_AD8]`
- `[_sama5d2x_pinmap.h:PIO_ADC_AD9]`
- `[_sama5d2x_pinmap.h:PIO_ADC_AD10]`
- `[_sama5d2x_pinmap.h:PIO_ADC_AD11]`
- `[_sama5d2x_pio.h:PIOA]`
- `[_sama5d2x_pio.h:PIOB]`
- `[_sama5d2x_pio.h:PIOC]`
- `[_sama5d2x_pio.h:PIOD]`
- `[_sama5d2x_pio.h:SAM_PIO_IOGROUP_OFFSET]`
- `[_sama5d2x_pio.h:SAM_PIO_IOGROUPA_OFFSET]`

## Invariants
- `[_sama5d2x_memorymap.h:#error]` Compile-time guard: CS0 FLASH size disagreement
- `[_sama5d3x_memorymap.h:#error]` Compile-time guard: CS0 FLASH size disagreement
- `[_sama5d4x_memorymap.h:#error]` Compile-time guard: CS0 FLASH size disagreement
- `[sam_classd.h:#error]` Compile-time guard: CONFIG_AUDIO is required for audio subsystem support
- `[sam_memorymap.h:#error]` Compile-time guard: Unrecognized SAMA5 architecture
- `[sam_mpddrc.h:#error]` Compile-time guard: Unrecognized SAMA5 architecture
- `[sam_pinmap.h:#error]` Compile-time guard: Unrecognized SAMA5 architecture
- `[sam_pio.h:#error]` Compile-time guard: Unrecognized SAMA5 architecture

## Side Effects
- None

## Verification
- Run: `make test`
