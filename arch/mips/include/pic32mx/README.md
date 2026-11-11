# pic32mx (`nuttx/arch/mips/include/pic32mx`)

## Overview
Hardware abstraction and architecture package for `pic32mx` under `nuttx/arch/mips/include/pic32mx`, providing 6 header file(s) and 0 source file(s) (including `chip.h`, `cp0.h`, `irq.h`, `irq_1xx2xx.h`).

## Interface
- `[chip.h:CHIP_PIC32MX1]`
- `[chip.h:CHIP_NPINS]`
- `[chip.h:CHIP_MHZ]`
- `[chip.h:CHIP_BOOTFLASH_KB]`
- `[chip.h:CHIP_PROGFLASH_KB]`
- `[chip.h:CHIP_DATAMEM_KB]`
- `[chip.h:CHIP_NPORTS]`
- `[chip.h:CHIP_NTIMERS]`
- `[chip.h:CHIP_NIC]`
- `[chip.h:CHIP_NOC]`
- `[chip.h:CHIP_NDMACH]`
- `[chip.h:CHIP_NUSBDMACHAN]`
- `[cp0.h:PIC32MX_CP0_HWRENA]`
- `[cp0.h:PIC32MX_CP0_BADVADDR]`
- `[cp0.h:PIC32MX_CP0_COUNT]`
- `[cp0.h:PIC32MX_CP0_COMPARE]`
- `[cp0.h:PIC32MX_CP0_STATUS]`
- `[cp0.h:PIC32MX_CP0_INTCTL]`
- `[cp0.h:PIC32MX_CP0_SRSCTL]`
- `[cp0.h:PIC32MX_CP0_SRSMAP]`
- `[cp0.h:PIC32MX_CP0_CAUSE]`
- `[cp0.h:PIC32MX_CP0_EPC]`
- `[cp0.h:PIC32MX_CP0_PRID]`
- `[cp0.h:PIC32MX_CP0_EBASE]`
- `[irq_1xx2xx.h:PIC32MX_IRQ_CT]`
- `[irq_1xx2xx.h:PIC32MX_IRQ_CS0]`
- `[irq_1xx2xx.h:PIC32MX_IRQ_CS1]`
- `[irq_1xx2xx.h:PIC32MX_IRQ_INT0]`
- `[irq_1xx2xx.h:PIC32MX_IRQ_T1]`
- `[irq_1xx2xx.h:PIC32MX_IRQ_IC1]`

## Invariants
- `[chip.h:#error]` Compile-time guard: Unrecognized PIC32 device
- `[irq.h:#error]` Compile-time guard: Unknown PIC32MX family

## Side Effects
- `[irq.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations

## Verification
- Run: `make test`
