# hardware (`nuttx/arch/risc-v/src/qemu-rv/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/risc-v/src/qemu-rv/hardware`, providing 4 header file(s) and 0 source file(s) (including `qemu_rv_aplic.h`, `qemu_rv_clint.h`, `qemu_rv_memorymap.h`, `qemu_rv_plic.h`).

## Interface
- `[qemu_rv_aplic.h:QEMU_RV_APLIC_NR_IRQ]`
- `[qemu_rv_clint.h:QEMU_RV_CLINT_MSIP]`
- `[qemu_rv_clint.h:QEMU_RV_CLINT_MTIMECMP]`
- `[qemu_rv_clint.h:QEMU_RV_CLINT_MTIME]`
- `[qemu_rv_clint.h:QEMU_RV_ACLINT_SSIP]`
- `[qemu_rv_clint.h:RISCV_CLINT_MSIP]`
- `[qemu_rv_clint.h:RISCV_ACLINT_SSIP]`
- `[qemu_rv_clint.h:RISCV_IPI]`
- `[qemu_rv_memorymap.h:QEMU_RV_PLIC_BASE]`
- `[qemu_rv_memorymap.h:QEMU_RV_CLINT_BASE]`
- `[qemu_rv_memorymap.h:QEMU_RV_ACLINT_BASE]`
- `[qemu_rv_memorymap.h:QEMU_RV_RESET_BASE]`
- `[qemu_rv_memorymap.h:QEMU_RV_APLIC_BASE]`
- `[qemu_rv_memorymap.h:QEMU_RV_IMSIC_BASE]`
- `[qemu_rv_plic.h:QEMU_RV_PLIC_PRIORITY]`
- `[qemu_rv_plic.h:QEMU_RV_PLIC_PENDING1]`
- `[qemu_rv_plic.h:QEMU_RV_PLIC_ENABLE1]`
- `[qemu_rv_plic.h:QEMU_RV_PLIC_ENABLE2]`
- `[qemu_rv_plic.h:QEMU_RV_PLIC_THRESHOLD]`
- `[qemu_rv_plic.h:QEMU_RV_PLIC_CLAIM]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
