# hardware (`nuttx/arch/arm/src/sam34/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/sam34/hardware`, providing 63 header file(s) and 0 source file(s) (including `sam3u_memorymap.h`, `sam3u_pinmap.h`, `sam3u_pio.h`, `sam3x_memorymap.h`).

## Interface
- `[sam3u_memorymap.h:SAM_CODE_BASE]`
- `[sam3u_memorymap.h:SAM_BOOTMEMORY_BASE]`
- `[sam3u_memorymap.h:SAM_INTFLASH0_BASE]`
- `[sam3u_memorymap.h:SAM_INTFLASH1_BASE]`
- `[sam3u_memorymap.h:SAM_INTROM_BASE]`
- `[sam3u_memorymap.h:SAM_INTSRAM_BASE]`
- `[sam3u_memorymap.h:SAM_INTSRAM0_BASE]`
- `[sam3u_memorymap.h:SAM_INTSRAM1_BASE]`
- `[sam3u_memorymap.h:SAM_NFCSRAM_BASE]`
- `[sam3u_memorymap.h:SAM_UDPHPSDMS_BASE]`
- `[sam3u_memorymap.h:SAM_BBSRAM_BASE]`
- `[sam3u_memorymap.h:SAM_PERIPHERALS_BASE]`
- `[sam3u_pinmap.h:GPIO_ADC0_AD0]`
- `[sam3u_pinmap.h:GPIO_ADC0_AD1]`
- `[sam3u_pinmap.h:GPIO_ADC0_AD2]`
- `[sam3u_pinmap.h:GPIO_ADC0_AD3]`
- `[sam3u_pinmap.h:GPIO_ADC0_AD4]`
- `[sam3u_pinmap.h:GPIO_ADC0_AD5]`
- `[sam3u_pinmap.h:GPIO_ADC0_AD6]`
- `[sam3u_pinmap.h:GPIO_ADC0_AD7]`
- `[sam3u_pinmap.h:GPIO_CAN_XCVR_RS]`
- `[sam3u_pinmap.h:GPIO_CAN1_XCVR_TXD]`
- `[sam3u_pinmap.h:GPIO_CAN1_XCVR_RXD]`
- `[sam3u_pinmap.h:GPIO_CAN2_XCVR_TXD]`
- `[sam3u_pio.h:SAM_PIO_PER_OFFSET]`
- `[sam3u_pio.h:SAM_PIO_PDR_OFFSET]`
- `[sam3u_pio.h:SAM_PIO_PSR_OFFSET]`
- `[sam3u_pio.h:SAM_PIO_OER_OFFSET]`
- `[sam3u_pio.h:SAM_PIO_ODR_OFFSET]`
- `[sam3u_pio.h:SAM_PIO_OSR_OFFSET]`

## Invariants
- `[sam_memorymap.h:#error]` Compile-time guard: Unrecognized SAM architecture
- `[sam_pinmap.h:#error]` Compile-time guard: Unrecognized SAM architecture
- `[sam_smc.h:#error]` Compile-time guard: Unrecognized SAM architecture

## Side Effects
- None

## Verification
- Run: `make test`
