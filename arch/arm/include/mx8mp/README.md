# mx8mp (`nuttx/arch/arm/include/mx8mp`)

## Overview
Hardware abstraction and architecture package for `mx8mp` under `nuttx/arch/arm/include/mx8mp`, providing 3 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`, `mx8mp_irq.h`).

## Interface
- `[chip.h:NVIC_SYSH_PRIORITY_MIN]`
- `[chip.h:NVIC_SYSH_PRIORITY_DEFAULT]`
- `[chip.h:NVIC_SYSH_PRIORITY_MAX]`
- `[chip.h:NVIC_SYSH_PRIORITY_STEP]`
- `[irq.h:MX8MP_IRQ_RESERVED]`
- `[irq.h:MX8MP_IRQ_NMI]`
- `[irq.h:MX8MP_IRQ_HARDFAULT]`
- `[irq.h:MX8MP_IRQ_MEMFAULT]`
- `[irq.h:MX8MP_IRQ_BUSFAULT]`
- `[irq.h:MX8MP_IRQ_USAGEFAULT]`
- `[irq.h:MX8MP_IRQ_SVCALL]`
- `[irq.h:MX8MP_IRQ_DBGMONITOR]`
- `[irq.h:MX8MP_IRQ_PENDSV]`
- `[irq.h:MX8MP_IRQ_SYSTICK]`
- `[irq.h:MX8MP_IRQ_FIRST]`
- `[mx8mp_irq.h:ARCH_ARM_INCLUDE_MX8MP_IRQ_H]`
- `[mx8mp_irq.h:MX8MP_IRQ_DAP]`
- `[mx8mp_irq.h:MX8MP_IRQ_SDMA1]`
- `[mx8mp_irq.h:MX8MP_IRQ_GPU3D]`
- `[mx8mp_irq.h:MX8MP_IRQ_SNVS_ONOFF]`
- `[mx8mp_irq.h:MX8MP_IRQ_LCDIF1]`
- `[mx8mp_irq.h:MX8MP_IRQ_LCDIF2]`
- `[mx8mp_irq.h:MX8MP_IRQ_VPU_G1]`
- `[mx8mp_irq.h:MX8MP_IRQ_VPU_G2]`
- `[mx8mp_irq.h:MX8MP_IRQ_QOS]`
- `[mx8mp_irq.h:MX8MP_IRQ_WDOG3]`
- `[mx8mp_irq.h:MX8MP_IRQ_HS_CP1]`

## Invariants
- `[irq.h:#error]` Compile-time guard: No IRQ numbers for this MX8Mx part

## Side Effects
- None

## Verification
- Run: `make test`
