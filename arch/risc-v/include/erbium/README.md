# erbium (`nuttx/arch/risc-v/include/erbium`)

## Overview
Hardware abstraction and architecture package for `erbium` under `nuttx/arch/risc-v/include/erbium`, providing 2 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`).

## Interface
- `[irq.h:RISCV_MAX_EXCEPTION]`
- `[irq.h:ERBIUM_IRQ_IBUSERR]`
- `[irq.h:ERBIUM_IRQ_IECCERR]`
- `[irq.h:ERBIUM_IRQ_LSPLITPF]`
- `[irq.h:ERBIUM_IRQ_SSPLITPF]`
- `[irq.h:ERBIUM_IRQ_MCODE]`
- `[irq.h:ERBIUM_FIRST_CUSTOM_EXCEPTION]`
- `[irq.h:ERBIUM_EXCEPTION_REASONS_16_19]`
- `[irq.h:RISCV_CUSTOM_EXCEPTION_REASONS]`
- `[irq.h:ERBIUM_IRQ_UART0]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
