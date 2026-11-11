# lm (`nuttx/arch/arm/src/tiva/hardware/lm`)

## Overview
Hardware abstraction and architecture package for `lm` under `nuttx/arch/arm/src/tiva/hardware/lm`, providing 14 header file(s) and 0 source file(s) (including `lm3s_ethernet.h`, `lm3s_flash.h`, `lm3s_gpio.h`, `lm3s_memorymap.h`).

## Interface
- `[lm3s_ethernet.h:TIVA_MAC_RIS_OFFSET]`
- `[lm3s_ethernet.h:TIVA_MAC_IACK_OFFSET]`
- `[lm3s_ethernet.h:TIVA_MAC_IM_OFFSET]`
- `[lm3s_ethernet.h:TIVA_MAC_RCTL_OFFSET]`
- `[lm3s_ethernet.h:TIVA_MAC_TCTL_OFFSET]`
- `[lm3s_ethernet.h:TIVA_MAC_DATA_OFFSET]`
- `[lm3s_ethernet.h:TIVA_MAC_IA0_OFFSET]`
- `[lm3s_ethernet.h:TIVA_MAC_IA1_OFFSET]`
- `[lm3s_ethernet.h:TIVA_MAC_THR_OFFSET]`
- `[lm3s_ethernet.h:TIVA_MAC_MCTL_OFFSET]`
- `[lm3s_ethernet.h:TIVA_MAC_MDV_OFFSET]`
- `[lm3s_ethernet.h:TIVA_MAC_MTXD_OFFSET]`
- `[lm3s_flash.h:TIVA_FLASH_NPAGES]`
- `[lm3s_flash.h:TIVA_FLASH_PAGESIZE]`
- `[lm3s_flash.h:TIVA_FLASH_SIZE]`
- `[lm3s_flash.h:TIVA_FLASH_FMA_OFFSET]`
- `[lm3s_flash.h:TIVA_FLASH_FMD_OFFSET]`
- `[lm3s_flash.h:TIVA_FLASH_FMC_OFFSET]`
- `[lm3s_flash.h:TIVA_FLASH_FCRIS_OFFSET]`
- `[lm3s_flash.h:TIVA_FLASH_FCIM_OFFSET]`
- `[lm3s_flash.h:TIVA_FLASH_FCMISC_OFFSET]`
- `[lm3s_flash.h:TIVA_FLASH_FMPRE_OFFSET]`
- `[lm3s_flash.h:TIVA_FLASH_FMPPE_OFFSET]`
- `[lm3s_flash.h:TIVA_FLASH_USECRL_OFFSET]`
- `[lm3s_gpio.h:TIVA_GPIOK_BASE]`
- `[lm3s_gpio.h:TIVA_GPIOL_BASE]`
- `[lm3s_gpio.h:TIVA_GPIOM_BASE]`
- `[lm3s_gpio.h:TIVA_GPION_BASE]`
- `[lm3s_gpio.h:TIVA_GPIOP_BASE]`
- `[lm3s_gpio.h:TIVA_GPIOQ_BASE]`

## Invariants
- `[lm3s_memorymap.h:#error]` Compile-time guard: Memory map not specified for this LM3S chip
- `[lm3s_pinmap.h:#error]` Compile-time guard: Unknown Stellaris chip
- `[lm4f_memorymap.h:#error]` Compile-time guard: Memory map not specified for this LM4F chip
- `[lm4f_pinmap.h:#error]` Compile-time guard: Unknown Stellaris chip

## Side Effects
- None

## Verification
- Run: `make test`
