# hardware (`nuttx/arch/arm/src/rtl8730e/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/rtl8730e/hardware`, providing 2 header file(s) and 0 source file(s) (including `rtl8730e_loguart.h`, `rtl8730e_memorymap.h`).

## Interface
- `[rtl8730e_loguart.h:RTL8730E_LOGUART_BASE]`
- `[rtl8730e_loguart.h:RTL8730E_LOGUART_RBR]`
- `[rtl8730e_loguart.h:RTL8730E_LOGUART_IER]`
- `[rtl8730e_loguart.h:RTL8730E_LOGUART_LSR]`
- `[rtl8730e_loguart.h:RTL8730E_LOGUART_THR3]`
- `[rtl8730e_loguart.h:LOGUART_IER_ERBI]`
- `[rtl8730e_loguart.h:LOGUART_LSR_DRDY]`
- `[rtl8730e_loguart.h:LOGUART_LSR_TP4F_NOT_FULL]`
- `[rtl8730e_loguart.h:LOGUART_LSR_TP4F_EMPTY]`
- `[rtl8730e_loguart.h:LOGUART_LSR_RXFIFO_INT]`
- `[rtl8730e_memorymap.h:ARMV7A_PGTABLE_MAPPING]`

## Invariants
- `[rtl8730e_memorymap.h:#error]` Compile-time guard: Only one of PGTABLE_BASE_PADDR or PGTABLE_BASE_VADDR is defined

## Side Effects
- None

## Verification
- Run: `make test`
