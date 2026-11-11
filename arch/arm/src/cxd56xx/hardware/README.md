# hardware (`nuttx/arch/arm/src/cxd56xx/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/cxd56xx/hardware`, providing 23 header file(s) and 0 source file(s) (including `cxd5602_backupmem.h`, `cxd5602_isop.h`, `cxd5602_isop_hadc0_highspeed.h`, `cxd5602_memorymap.h`).

## Interface
- `[cxd5602_backupmem.h:backup_info_t]`
- `[cxd5602_backupmem.h:CXD56_BKUP_SRAM_BASE]`
- `[cxd5602_backupmem.h:BKUP]`
- `[cxd5602_memorymap.h:CXD56_ADSP_BASE]`
- `[cxd5602_memorymap.h:CXD56_SYS_MIRROR]`
- `[cxd5602_memorymap.h:CXD56_SYS_RAM_BASE]`
- `[cxd5602_memorymap.h:CXD56_GDSP_RAM_BASE]`
- `[cxd5602_memorymap.h:CXD56_ADSP_RAM_BASE]`
- `[cxd5602_memorymap.h:CXD56_RAM_BASE]`
- `[cxd5602_memorymap.h:CXD56_RAM_SIZE]`
- `[cxd5602_memorymap.h:CXD56_ARM_BASE]`
- `[cxd5602_memorymap.h:CXD56_TIMER_BASE]`
- `[cxd5602_memorymap.h:CXD56_WDOG_BASE]`
- `[cxd5602_memorymap.h:CXD56_INTC_BASE]`
- `[cxd5602_memorymap.h:CXD56_SWINT_BASE]`
- `[cxd5602_pinconfig.h:PINCONF]`
- `[cxd5602_pinconfig.h:PINCONF_I2C4_BCK_GPIO]`
- `[cxd5602_pinconfig.h:PINCONF_I2C4_BCK]`
- `[cxd5602_pinconfig.h:PINCONF_I2C4_BDT_GPIO]`
- `[cxd5602_pinconfig.h:PINCONF_I2C4_BDT]`
- `[cxd5602_pinconfig.h:PINCONF_PMIC_INT_GPIO]`
- `[cxd5602_pinconfig.h:PINCONF_PMIC_INT]`
- `[cxd5602_pinconfig.h:PINCONF_PMIC_INT_OD]`
- `[cxd5602_pinconfig.h:PINCONF_RTC_IRQ_OUT_GPIO]`
- `[cxd5602_pinconfig.h:PINCONF_RTC_IRQ_OUT]`
- `[cxd5602_pinconfig.h:PINCONF_RTC_IRQ_OUT_OD]`
- `[cxd5602_pinconfig.h:PINCONF_AP_CLK_GPIO]`
- `[cxd5602_topreg.h:CXD56_TOPREG_PWD_CTL]`
- `[cxd5602_topreg.h:CXD56_TOPREG_ANA_PW_CTL]`
- `[cxd5602_topreg.h:CXD56_TOPREG_ANA_EN_CTL]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
