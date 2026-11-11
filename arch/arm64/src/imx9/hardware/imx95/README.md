# imx95 (`nuttx/arch/arm64/src/imx9/hardware/imx95`)

## Overview
Hardware abstraction and architecture package for `imx95` under `nuttx/arch/arm64/src/imx9/hardware/imx95`, providing 7 header file(s) and 0 source file(s) (including `imx95_ccm.h`, `imx95_clock.h`, `imx95_gpio.h`, `imx95_iomuxc.h`).

## Interface
- `[imx95_ccm.h:ccm_clock_name_e]`
- `[imx95_ccm.h:IMX9_CCM_CR_CTRL_OFFSET]`
- `[imx95_ccm.h:IMX9_CCM_CR_CTRL_SET_OFFSET]`
- `[imx95_ccm.h:IMX9_CCM_CR_CTRL_CLR_OFFSET]`
- `[imx95_ccm.h:IMX9_CCM_CR_CTRL_TOG_OFFSET]`
- `[imx95_ccm.h:IMX9_CCM_CR_STAT0_OFFSET]`
- `[imx95_ccm.h:IMX9_CCM_CR_AUTH_OFFSET]`
- `[imx95_ccm.h:IMX9_CCM_CR_AUTH_SET_OFFSET]`
- `[imx95_ccm.h:IMX9_CCM_CR_AUTH_CLR_OFFSET]`
- `[imx95_ccm.h:IMX9_CCM_CR_AUTH_TOG_OFFSET]`
- `[imx95_ccm.h:IMX9_CCM_GPR_SH_OFFSET]`
- `[imx95_ccm.h:IMX9_CCM_GPR_SH_SET_OFFSET]`
- `[imx95_ccm.h:IMX9_CCM_GPR_SH_CLR_OFFSET]`
- `[imx95_clock.h:clock_id_e]`
- `[imx95_clock.h:clock_config_t]`
- `[imx95_clock.h:CCM_CR_COUNT]`
- `[imx95_clock.h:ROOT_CLOCK_OFFSET]`
- `[imx95_clock.h:CLOCK_DIV_SHIFT]`
- `[imx95_clock.h:CLOCK_DIV_MASK]`
- `[imx95_clock.h:CLOCK_DIV]`
- `[imx95_clock.h:GET_DIV]`
- `[imx95_clock.h:ROOT_SHIFT]`
- `[imx95_clock.h:ROOT_MASK]`
- `[imx95_clock.h:ROOT]`
- `[imx95_clock.h:GET_ROOT]`
- `[imx95_clock.h:ID_SHIFT]`
- `[imx95_clock.h:ID_MASK]`
- `[imx95_gpio.h:IMX9_GPIO_VERID_OFFSET]`
- `[imx95_gpio.h:IMX9_GPIO_PARAM_OFFSET]`
- `[imx95_gpio.h:IMX9_GPIO_LOCK_OFFSET]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
