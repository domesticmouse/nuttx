# gdble (`nuttx/arch/risc-v/src/gd32vw55x/gdble`)

## Overview
Hardware abstraction and architecture package for `gdble` under `nuttx/arch/risc-v/src/gd32vw55x/gdble`, providing 0 header file(s) and 1 source file(s) (including `gd32_ble.c`).

## Interface
- `[gd32_ble.c:gd32_ble_initialize]`

## Invariants
- None

## Side Effects
- `[gd32_ble.c:irq_attach]` Registers hardware interrupt service routines with the kernel IRQ dispatcher (`irq_attach`)

## Verification
- Run: `make test`
