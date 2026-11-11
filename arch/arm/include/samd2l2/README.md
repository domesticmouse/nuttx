# samd2l2 (`nuttx/arch/arm/include/samd2l2`)

## Overview
Hardware abstraction and architecture package for `samd2l2` under `nuttx/arch/arm/include/samd2l2`, providing 6 header file(s) and 0 source file(s) (including `chip.h`, `irq.h`, `sam_adc.h`, `samd20_irq.h`).

## Interface
- `[chip.h:SAMD20]`
- `[chip.h:SAMD20E]`
- `[chip.h:SAMD2L2_FLASH_SIZE]`
- `[chip.h:SAMD2L2_SRAM0_SIZE]`
- `[chip.h:SAMD2L2_LPRAM_SIZE]`
- `[irq.h:SAM_IRQ_RESERVED]`
- `[irq.h:SAM_IRQ_NMI]`
- `[irq.h:SAM_IRQ_HARDFAULT]`
- `[irq.h:SAM_IRQ_SVCALL]`
- `[irq.h:SAM_IRQ_PENDSV]`
- `[irq.h:SAM_IRQ_SYSTICK]`
- `[irq.h:SAM_IRQ_INTERRUPT]`
- `[sam_adc.h:sam_adc_param_s]`
- `[sam_adc.h:SAMD_ADC_IOCTL_START]`
- `[sam_adc.h:SAMD_ADC_IOCTL_STOP]`
- `[sam_adc.h:SAMD_ADC_IOCTL_SET_PARAMS]`
- `[sam_adc.h:SAMD_ADC_IOCTL_GET_PARAMS]`
- `[samd20_irq.h:SAM_IRQ_PM]`
- `[samd20_irq.h:SAM_IRQ_SYSCTRL]`
- `[samd20_irq.h:SAM_IRQ_WDT]`
- `[samd20_irq.h:SAM_IRQ_RTC]`
- `[samd20_irq.h:SAM_IRQ_EIC]`
- `[samd20_irq.h:SAM_IRQ_NVMCTRL]`
- `[samd20_irq.h:SAM_IRQ_EVSYS]`
- `[samd20_irq.h:SAM_IRQ_SERCOM0]`
- `[samd20_irq.h:SAM_IRQ_SERCOM1]`
- `[samd20_irq.h:SAM_IRQ_SERCOM2]`
- `[samd20_irq.h:SAM_IRQ_SERCOM3]`
- `[samd20_irq.h:SAM_IRQ_SERCOM4]`
- `[samd21_irq.h:SAM_IRQ_PM]`

## Invariants
- `[irq.h:#error]` Compile-time guard: Unrecognized SAMD/L architecture

## Side Effects
- None

## Verification
- Run: `make test`
