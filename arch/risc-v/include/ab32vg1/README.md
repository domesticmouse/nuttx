# ab32vg1 (`nuttx/arch/risc-v/include/ab32vg1`)

## Overview
Hardware abstraction and architecture package for `ab32vg1` under `nuttx/arch/risc-v/include/ab32vg1`, providing 2 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`).

## Interface
- `[chip.h:AB32VG1_SRAM_BASE]`
- `[chip.h:AB32VG1_SRAM_SIZE]`
- `[chip.h:AB32VG1_AECRAM_BASE]`
- `[chip.h:AB32VG1_AECRAM_SIZE]`
- `[chip.h:AB32VG1_ICRAM_BASE]`
- `[chip.h:AB32VG1_ICRAM_SIZE]`
- `[irq.h:AB32VG1_IRQ_FIRST]`
- `[irq.h:AB32VG1_IRQ_SW]`
- `[irq.h:AB32VG1_IRQ_TMR0]`
- `[irq.h:AB32VG1_IRQ_TMR1]`
- `[irq.h:AB32VG1_IRQ_TMR245]`
- `[irq.h:AB32VG1_IRQ_IRRX]`
- `[irq.h:AB32VG1_IRQ_USB]`
- `[irq.h:AB32VG1_IRQ_SD]`
- `[irq.h:AB32VG1_IRQ_AUBUF]`
- `[irq.h:AB32VG1_IRQ_SDADC]`
- `[irq.h:AB32VG1_IRQ_AUDEC]`
- `[irq.h:AB32VG1_IRQ_SRC]`

## Invariants
- None

## Side Effects
- `[irq.h:__asm__]` Executes inline architecture-specific assembly instructions and barrier operations

## Verification
- Run: `make test`
