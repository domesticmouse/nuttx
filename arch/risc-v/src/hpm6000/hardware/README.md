# hardware (`nuttx/arch/risc-v/src/hpm6000/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/risc-v/src/hpm6000/hardware`, providing 8 header file(s) and 0 source file(s) (including `hpm_gpio.h`, `hpm_ioc.h`, `hpm_mchtmr.h`, `hpm_memorymap.h`).

## Subdirectories & Boundaries
- `hpm6300`: [./hpm6300/README.md](./hpm6300/README.md) - Hardware abstraction and architecture package for `hpm6300` under `nuttx/arch/risc-v/src/hpm6000/hardware/hpm6300`, providing 6 header file(s) and 0 source file(s) (including `hpm6300_gpio.h`, `hpm6300_ioc.h`, `hpm6300_memorymap.h`, `hpm6300_pcfg.h`).

## Interface
- `[hpm_gpio.h:GPIOA]`
- `[hpm_gpio.h:GPIOB]`
- `[hpm_gpio.h:GPIOC]`
- `[hpm_gpio.h:GPIOD]`
- `[hpm_gpio.h:GPIOE]`
- `[hpm_gpio.h:GPIOF]`
- `[hpm_gpio.h:GPIOX]`
- `[hpm_gpio.h:GPIOY]`
- `[hpm_gpio.h:GPIOZ]`
- `[hpm_gpio.h:HPM_GPIO_NPINS]`
- `[hpm_gpio.h:GPIO_PIN]`
- `[hpm_ioc.h:CONFIG_ARCH_FAMILY_HPM6300]`
- `[hpm_ioc.h:DRIVE_260OHM]`
- `[hpm_ioc.h:DRIVE_130OHM]`
- `[hpm_ioc.h:DRIVE_88OHM]`
- `[hpm_ioc.h:DRIVE_65OHM]`
- `[hpm_ioc.h:DRIVE_52OHM]`
- `[hpm_ioc.h:DRIVE_43OHM]`
- `[hpm_ioc.h:DRIVE_37OHM]`
- `[hpm_ioc.h:SPEED_SLOW]`
- `[hpm_ioc.h:SPEED_MEDIUM]`
- `[hpm_ioc.h:SPEED_FAST]`
- `[hpm_ioc.h:SPEED_MAX]`
- `[hpm_mchtmr.h:HPM_MCHTMR_MTIME]`
- `[hpm_mchtmr.h:HPM_MCHTMR_MTIMECMP]`
- `[hpm_memorymap.h:CONFIG_ARCH_FAMILY_HPM6300]`
- `[hpm_plic.h:HPM_PLIC_PRIORITY]`
- `[hpm_plic.h:HPM_PLIC_PENDING0]`
- `[hpm_plic.h:HPM_PLIC_PENDING1]`
- `[hpm_plic.h:HPM_PLIC_PENDING2]`
- [./hpm6300/README.md](./hpm6300/README.md)

## Invariants
- `[hpm_gpio.h:#error]` Compile-time guard: The selected HPM variant is not implemented
- `[hpm_ioc.h:#error]` Compile-time guard: Unrecognized HPM chip
- `[hpm_memorymap.h:#error]` Compile-time guard: Unrecognized HPM architecture
- `[hpm_sysctl.h:#error]` Compile-time guard: Unrecognized HPM architecture

## Side Effects
- None

## Verification
- Run: `make test`
