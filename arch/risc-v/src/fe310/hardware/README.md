# hardware (`nuttx/arch/risc-v/src/fe310/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/risc-v/src/fe310/hardware`, providing 6 header file(s) and 0 source file(s) (including `fe310_clint.h`, `fe310_gpio.h`, `fe310_memorymap.h`, `fe310_plic.h`).

## Interface
- `[fe310_clint.h:FE310_CLINT_MTIMECMP]`
- `[fe310_clint.h:FE310_CLINT_MTIME]`
- `[fe310_gpio.h:FE310_GPIO_INPUT_VAL]`
- `[fe310_gpio.h:FE310_GPIO_INPUT_EN]`
- `[fe310_gpio.h:FE310_GPIO_OUTPUT_EN]`
- `[fe310_gpio.h:FE310_GPIO_OUTPUT_VAL]`
- `[fe310_gpio.h:FE310_GPIO_PU_EN]`
- `[fe310_gpio.h:FE310_GPIO_DS]`
- `[fe310_gpio.h:FE310_GPIO_RISE_IE]`
- `[fe310_gpio.h:FE310_GPIO_RISE_IP]`
- `[fe310_gpio.h:FE310_GPIO_FALL_IE]`
- `[fe310_gpio.h:FE310_GPIO_FALL_IP]`
- `[fe310_gpio.h:FE310_GPIO_HIGH_IE]`
- `[fe310_gpio.h:FE310_GPIO_HIGH_IP]`
- `[fe310_memorymap.h:FE310_CLINT_BASE]`
- `[fe310_memorymap.h:FE310_PLIC_BASE]`
- `[fe310_memorymap.h:FE310_PRCI_BASE]`
- `[fe310_memorymap.h:FE310_GPIO_BASE]`
- `[fe310_memorymap.h:FE310_UART0_BASE]`
- `[fe310_memorymap.h:FE310_QSPI0_BASE]`
- `[fe310_memorymap.h:FE310_UART1_BASE]`
- `[fe310_plic.h:FE310_PLIC_PRIORITY]`
- `[fe310_plic.h:FE310_PLIC_PENDING1]`
- `[fe310_plic.h:FE310_PLIC_ENABLE1]`
- `[fe310_plic.h:FE310_PLIC_ENABLE2]`
- `[fe310_plic.h:FE310_PLIC_THRESHOLD]`
- `[fe310_plic.h:FE310_PLIC_CLAIM]`
- `[fe310_prci.h:FE310_HFROSCCFG]`
- `[fe310_prci.h:FE310_HFXOSCCFG]`
- `[fe310_prci.h:FE310_PLLCFG]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
