# hardware (`nuttx/arch/risc-v/src/k210/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/risc-v/src/k210/hardware`, providing 6 header file(s) and 0 source file(s) (including `k210_clint.h`, `k210_memorymap.h`, `k210_plic.h`, `k210_sysctl.h`).

## Interface
- `[k210_clint.h:K210_CLINT_MSIP]`
- `[k210_clint.h:K210_CLINT_MTIMECMP]`
- `[k210_clint.h:K210_CLINT_MTIME]`
- `[k210_clint.h:RISCV_CLINT_MSIP]`
- `[k210_clint.h:RISCV_IPI]`
- `[k210_memorymap.h:K210_CLINT_BASE]`
- `[k210_memorymap.h:K210_PLIC_BASE]`
- `[k210_memorymap.h:K210_UART0_BASE]`
- `[k210_memorymap.h:K210_GPIOHS_BASE]`
- `[k210_memorymap.h:K210_FPIOA_BASE]`
- `[k210_memorymap.h:K210_WDT0_BASE]`
- `[k210_memorymap.h:K210_WDT1_BASE]`
- `[k210_memorymap.h:K210_SYSCTL_BASE]`
- `[k210_plic.h:K210_PLIC_PRIORITY]`
- `[k210_plic.h:K210_PLIC_PENDING1]`
- `[k210_plic.h:K210_PLIC_ENABLE1]`
- `[k210_plic.h:K210_PLIC_ENABLE2]`
- `[k210_plic.h:K210_PLIC_THRESHOLD]`
- `[k210_plic.h:K210_PLIC_CLAIM]`
- `[k210_sysctl.h:K210_SYSCTL_GIT_ID]`
- `[k210_sysctl.h:K210_SYSCTL_CLK_FREQ]`
- `[k210_sysctl.h:K210_SYSCTL_PLL0]`
- `[k210_sysctl.h:K210_SYSCTL_PLL1]`
- `[k210_sysctl.h:K210_SYSCTL_PLL2]`
- `[k210_sysctl.h:K210_SYSCTL_PLL_LOCK]`
- `[k210_sysctl.h:K210_SYSCTL_ROM_ERROR]`
- `[k210_sysctl.h:K210_SYSCTL_CLKSEL0]`
- `[k210_sysctl.h:K210_SYSCTL_CLKSEL1]`
- `[k210_sysctl.h:K210_SYSCTL_CLK_EN_CENT]`
- `[k210_sysctl.h:K210_SYSCTL_CLK_EN_PERI]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
