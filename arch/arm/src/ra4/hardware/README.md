# hardware (`nuttx/arch/arm/src/ra4/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/ra4/hardware`, providing 15 header file(s) and 0 source file(s) (including `ra4m1_icu.h`, `ra4m1_memorymap.h`, `ra4m1_mstp.h`, `ra4m1_pinmap.h`).

## Interface
- `[ra4m1_icu.h:EVENT_NONE]`
- `[ra4m1_icu.h:EVENT_ICU_IRQ0]`
- `[ra4m1_icu.h:EVENT_ICU_IRQ1]`
- `[ra4m1_icu.h:EVENT_ICU_IRQ2]`
- `[ra4m1_icu.h:EVENT_ICU_IRQ3]`
- `[ra4m1_icu.h:EVENT_ICU_IRQ4]`
- `[ra4m1_icu.h:EVENT_ICU_IRQ5]`
- `[ra4m1_icu.h:EVENT_ICU_IRQ6]`
- `[ra4m1_icu.h:EVENT_ICU_IRQ7]`
- `[ra4m1_icu.h:EVENT_ICU_IRQ8]`
- `[ra4m1_icu.h:EVENT_ICU_IRQ9]`
- `[ra4m1_icu.h:EVENT_ICU_IRQ10]`
- `[ra4m1_memorymap.h:R_ACMPLP_BASE]`
- `[ra4m1_memorymap.h:R_ADC0_BASE]`
- `[ra4m1_memorymap.h:R_ADC1_BASE]`
- `[ra4m1_memorymap.h:R_BUS_BASE]`
- `[ra4m1_memorymap.h:R_CAC_BASE]`
- `[ra4m1_memorymap.h:R_CAN0_BASE]`
- `[ra4m1_memorymap.h:R_CAN1_BASE]`
- `[ra4m1_memorymap.h:R_CRC_BASE]`
- `[ra4m1_memorymap.h:R_CTSU_BASE]`
- `[ra4m1_memorymap.h:R_DAC_BASE]`
- `[ra4m1_memorymap.h:R_DAC8_BASE]`
- `[ra4m1_memorymap.h:R_DEBUG_BASE]`
- `[ra4m1_mstp.h:R_MSTP_MSTPCRB_OFFSET]`
- `[ra4m1_mstp.h:R_MSTP_MSTPCRC_OFFSET]`
- `[ra4m1_mstp.h:R_MSTP_MSTPCRD_OFFSET]`
- `[ra4m1_mstp.h:R_MSTP_MSTPCRB]`
- `[ra4m1_mstp.h:R_MSTP_MSTPCRC]`
- `[ra4m1_mstp.h:R_MSTP_MSTPCRD]`

## Invariants
- `[ra4m1_icu.h:#error]` Compile-time guard: Unsupported RA memory map
- `[ra_icu.h:#error]` Compile-time guard: Unsupported RA memory map
- `[ra_memorymap.h:#error]` Compile-time guard: Unsupported RA memory map
- `[ra_mstp.h:#error]` Compile-time guard: Unsupported RA Module Stop Control map
- `[ra_option_setting.h:#error]` Compile-time guard: Unsupported RA memory map
- `[ra_pinmap.h:#error]` Compile-time guard: Unsupported RA memory map

## Side Effects
- None

## Verification
- Run: `make test`
