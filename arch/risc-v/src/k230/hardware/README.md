# hardware (`nuttx/arch/risc-v/src/k230/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/risc-v/src/k230/hardware`, providing 3 header file(s) and 0 source file(s) (including `k230_clint.h`, `k230_memorymap.h`, `k230_plic.h`).

## Interface
- `[k230_clint.h:K230_CLINT_MSIP]`
- `[k230_clint.h:K230_CLINT_MTIMECMP]`
- `[k230_clint.h:K230_CLINT_SSIP]`
- `[k230_clint.h:K230_CLINT_STIMECMP]`
- `[k230_clint.h:K230_CLINT_MTIME]`
- `[k230_clint.h:K230_CLINT_STIME]`
- `[k230_clint.h:K230_CLINT_FREQ]`
- `[k230_clint.h:K230_IPI]`
- `[k230_clint.h:K230_TIME]`
- `[k230_clint.h:K230_TIMECMP]`
- `[k230_memorymap.h:K230_PLIC_BASE]`
- `[k230_memorymap.h:K230_CLINT_BASE]`
- `[k230_memorymap.h:K230_CPU1_BOOTA]`
- `[k230_memorymap.h:K230_CPU1_RESET]`
- `[k230_memorymap.h:CSR_MENVCFG]`
- `[k230_memorymap.h:CSR_MXSTATUS]`
- `[k230_memorymap.h:CSR_MHCR]`
- `[k230_memorymap.h:CSR_MCOR]`
- `[k230_memorymap.h:CSR_MCCR2]`
- `[k230_memorymap.h:CSR_MHINT]`
- `[k230_memorymap.h:CSR_MSMPR]`
- `[k230_memorymap.h:CSR_PLIC_BASE]`
- `[k230_plic.h:K230_PLIC_PRIORITY]`
- `[k230_plic.h:K230_PLIC_PENDING1]`
- `[k230_plic.h:K230_PLIC_ENABLE1]`
- `[k230_plic.h:K230_PLIC_ENABLE2]`
- `[k230_plic.h:K230_PLIC_THRESHOLD]`
- `[k230_plic.h:K230_PLIC_CLAIM]`
- `[k230_plic.h:K230_PLIC_CTRL]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
