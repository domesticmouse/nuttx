# hardware (`nuttx/arch/arm/src/ht32f491x3/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/ht32f491x3/hardware`, providing 7 header file(s) and 0 source file(s) (including `ht32f491x3_crm.h`, `ht32f491x3_flash.h`, `ht32f491x3_gpio.h`, `ht32f491x3_memorymap.h`).

## Interface
- `[ht32f491x3_crm.h:HT32_CRM_CTRL_OFFSET]`
- `[ht32f491x3_crm.h:HT32_CRM_PLLCFG_OFFSET]`
- `[ht32f491x3_crm.h:HT32_CRM_CFG_OFFSET]`
- `[ht32f491x3_crm.h:HT32_CRM_CLKINT_OFFSET]`
- `[ht32f491x3_crm.h:HT32_CRM_AHBRST1_OFFSET]`
- `[ht32f491x3_crm.h:HT32_CRM_AHBRST2_OFFSET]`
- `[ht32f491x3_crm.h:HT32_CRM_AHBRST3_OFFSET]`
- `[ht32f491x3_crm.h:HT32_CRM_APB1RST_OFFSET]`
- `[ht32f491x3_crm.h:HT32_CRM_APB2RST_OFFSET]`
- `[ht32f491x3_crm.h:HT32_CRM_AHBEN1_OFFSET]`
- `[ht32f491x3_crm.h:HT32_CRM_AHBEN2_OFFSET]`
- `[ht32f491x3_crm.h:HT32_CRM_AHBEN3_OFFSET]`
- `[ht32f491x3_flash.h:HT32_FLASH_PSR_OFFSET]`
- `[ht32f491x3_flash.h:HT32_FLASH_PSR]`
- `[ht32f491x3_flash.h:HT32_FLASH_PSR_PROGRAM]`
- `[ht32f491x3_flash.h:HT32_FLASH_WAIT_CYCLE_0]`
- `[ht32f491x3_flash.h:HT32_FLASH_WAIT_CYCLE_1]`
- `[ht32f491x3_flash.h:HT32_FLASH_WAIT_CYCLE_2]`
- `[ht32f491x3_flash.h:HT32_FLASH_WAIT_CYCLE_3]`
- `[ht32f491x3_flash.h:HT32_FLASH_WAIT_CYCLE_4]`
- `[ht32f491x3_gpio.h:HT32_GPIO_CFGR_OFFSET]`
- `[ht32f491x3_gpio.h:HT32_GPIO_OMODE_OFFSET]`
- `[ht32f491x3_gpio.h:HT32_GPIO_ODRVR_OFFSET]`
- `[ht32f491x3_gpio.h:HT32_GPIO_PULL_OFFSET]`
- `[ht32f491x3_gpio.h:HT32_GPIO_IDT_OFFSET]`
- `[ht32f491x3_gpio.h:HT32_GPIO_ODT_OFFSET]`
- `[ht32f491x3_gpio.h:HT32_GPIO_SCR_OFFSET]`
- `[ht32f491x3_gpio.h:HT32_GPIO_WPR_OFFSET]`
- `[ht32f491x3_gpio.h:HT32_GPIO_MUXL_OFFSET]`
- `[ht32f491x3_gpio.h:HT32_GPIO_MUXH_OFFSET]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
