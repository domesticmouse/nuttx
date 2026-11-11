# pic32mz (`nuttx/arch/mips/include/pic32mz`)

## Overview
Hardware abstraction and architecture package for `pic32mz` under `nuttx/arch/mips/include/pic32mz`, providing 6 header file(s) and 0 source file(s) (including `chip.h`, `cp0.h`, `irq.h`, `irq_pic32mzw1.h`).

## Interface
- `[chip.h:CHIP_PIC32MZEC]`
- `[chip.h:CHIP_BOOTFLASH_KB]`
- `[chip.h:CHIP_PROGFLASH_KB]`
- `[chip.h:CHIP_DATAMEM_KB]`
- `[chip.h:CHIP_NTIMERS]`
- `[chip.h:CHIP_NIC]`
- `[chip.h:CHIP_NOC]`
- `[chip.h:CHIP_NUARTS]`
- `[chip.h:CHIP_UARTFIFOD]`
- `[chip.h:CHIP_NSPI]`
- `[chip.h:CHIP_NCAN]`
- `[chip.h:CHIP_NCRTYPO]`
- `[cp0.h:PIC32MZ_CP0_INDEX]`
- `[cp0.h:PIC32MZ_CP0_RANDOM]`
- `[cp0.h:PIC32MZ_CP0_ENTRYLO0]`
- `[cp0.h:PIC32MZ_CP0_ENTRYLO1]`
- `[cp0.h:PIC32MZ_CP0_CONTEXT]`
- `[cp0.h:PIC32MZ_CP0_USERLOCAL]`
- `[cp0.h:PIC32MZ_CP0_PAGEMASK]`
- `[cp0.h:PIC32MZ_CP0_PAGEGRAIN]`
- `[cp0.h:PIC32MZ_CP0_WIRED]`
- `[cp0.h:PIC32MZ_CP0_HWRENA]`
- `[cp0.h:PIC32MZ_CP0_BADVADDR]`
- `[cp0.h:PIC32MZ_CP0_COUNT]`
- `[irq_pic32mzw1.h:PIC32MZ_IRQ_CT]`
- `[irq_pic32mzw1.h:PIC32MZ_IRQ_CS0]`
- `[irq_pic32mzw1.h:PIC32MZ_IRQ_CS1]`
- `[irq_pic32mzw1.h:PIC32MZ_IRQ_INT0]`
- `[irq_pic32mzw1.h:PIC32MZ_IRQ_T1]`
- `[irq_pic32mzw1.h:PIC32MZ_IRQ_ICE1]`

## Invariants
- `[chip.h:#error]` Compile-time guard: Unrecognized PIC32MZ device
- `[irq.h:#error]` Compile-time guard: Unknown PIC32MZ family

## Side Effects
- `[irq.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations

## Verification
- Run: `make test`
