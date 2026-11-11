# eic7700x (`nuttx/arch/risc-v/include/eic7700x`)

## Overview
Hardware abstraction and architecture package for `eic7700x` under `nuttx/arch/risc-v/include/eic7700x`, providing 4 header file(s) and 0 source file(s) (including `chip.h`, `eic7700x_pinctrl.h`, `eic7700x_reset.h`, `irq.h`).

## Interface
- `[eic7700x_pinctrl.h:eic7700x_pad_e]`
- `[eic7700x_pinctrl.h:EIC7700X_PAD_NPADS]`
- `[eic7700x_pinctrl.h:EIC7700X_PAD_OFFSET]`
- `[eic7700x_pinctrl.h:EIC7700X_PAD_CHIP_MODE_FUNC_CHIP_MODE]`
- `[eic7700x_pinctrl.h:EIC7700X_PAD_MODE_SET0_FUNC_SDIO0_DETECT]`
- `[eic7700x_pinctrl.h:EIC7700X_PAD_MODE_SET0_FUNC_GPIO13]`
- `[eic7700x_pinctrl.h:EIC7700X_PAD_MODE_SET1_FUNC_SDIO0_WRITE_PROT]`
- `[eic7700x_pinctrl.h:EIC7700X_PAD_MODE_SET1_FUNC_GPIO14]`
- `[eic7700x_pinctrl.h:EIC7700X_PAD_MODE_SET2_FUNC_SDIO1_DETECT]`
- `[eic7700x_pinctrl.h:EIC7700X_PAD_MODE_SET2_FUNC_GPIO15]`
- `[eic7700x_pinctrl.h:EIC7700X_PAD_MODE_SET3_FUNC_SDIO1_WRITE_PROT]`
- `[eic7700x_pinctrl.h:EIC7700X_PAD_MODE_SET3_FUNC_GPIO16]`
- `[eic7700x_pinctrl.h:EIC7700X_PAD_XIN_FUNC_XIN_24M]`
- `[eic7700x_reset.h:eic7700x_reset_e]`
- `[eic7700x_reset.h:EIC7700X_RESET_CONTROLLER]`
- `[eic7700x_reset.h:EIC7700X_RESET_NREGS]`
- `[eic7700x_reset.h:EIC7700X_RESET_ID]`
- `[eic7700x_reset.h:EIC7700X_RESET_REGOF]`
- `[eic7700x_reset.h:EIC7700X_RESET_BITOF]`
- `[irq.h:EIC7700X_PLIC_IRQS]`
- `[irq.h:NR_IRQS]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
