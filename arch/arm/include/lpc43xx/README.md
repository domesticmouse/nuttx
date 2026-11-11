# lpc43xx (`nuttx/arch/arm/include/lpc43xx`)

## Overview
Hardware abstraction and architecture package for `lpc43xx` under `nuttx/arch/arm/include/lpc43xx`, providing 2 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`).

## Interface
- `[chip.h:LPC43_FLASH_BANKA_SIZE]`
- `[chip.h:LPC43_FLASH_BANKB_SIZE]`
- `[chip.h:LPC43_LOCSRAM_BANK0_SIZE]`
- `[chip.h:LPC43_LOCSRAM_BANK1_SIZE]`
- `[chip.h:LPC43_AHBSRAM_BANK0_SIZE]`
- `[chip.h:LPC43_AHBSRAM_BANK1_SIZE]`
- `[chip.h:LPC43_AHBSRAM_BANK2_SIZE]`
- `[chip.h:LPC43_EEPROM_SIZE]`
- `[chip.h:LPC43_MCPWM]`
- `[chip.h:LPC43_NUSARTS]`
- `[chip.h:LPC43_NSSP]`
- `[chip.h:LPC43_NTIMERS]`
- `[irq.h:LPC43_IRQ_RESERVED]`
- `[irq.h:LPC43_IRQ_NMI]`
- `[irq.h:LPC43_IRQ_HARDFAULT]`
- `[irq.h:LPC43_IRQ_MEMFAULT]`
- `[irq.h:LPC43_IRQ_BUSFAULT]`
- `[irq.h:LPC43_IRQ_USAGEFAULT]`
- `[irq.h:LPC43_IRQ_SIGNVALUE]`
- `[irq.h:LPC43_IRQ_SVCALL]`
- `[irq.h:LPC43_IRQ_DBGMONITOR]`
- `[irq.h:LPC43_IRQ_PENDSV]`
- `[irq.h:LPC43_IRQ_SYSTICK]`
- `[irq.h:LPC43_IRQ_EXTINT]`

## Invariants
- `[chip.h:#error]` Compile-time guard: Unsupported LPC43xx chip

## Side Effects
- None

## Verification
- Run: `make test`
