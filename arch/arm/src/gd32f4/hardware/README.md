# hardware (`nuttx/arch/arm/src/gd32f4/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/gd32f4/hardware`, providing 16 header file(s) and 0 source file(s) (including `gd32f450_memorymap.h`, `gd32f450_pinmap.h`, `gd32f4xx_dma.h`, `gd32f4xx_enet.h`).

## Interface
- `[gd32f450_memorymap.h:GD32_CODE_BASE]`
- `[gd32f450_memorymap.h:GD32_SRAM_BASE]`
- `[gd32f450_memorymap.h:GD32_PERIPH_BASE]`
- `[gd32f450_memorymap.h:GD32_EXMC_REG_BASE]`
- `[gd32f450_memorymap.h:GD32_EXMC_BASE]`
- `[gd32f450_memorymap.h:GD32_EXMC_BANK0]`
- `[gd32f450_memorymap.h:GD32_EXMC_BANK1]`
- `[gd32f450_memorymap.h:GD32_EXMC_BANK2]`
- `[gd32f450_memorymap.h:GD32_EXMC_BANK3]`
- `[gd32f450_memorymap.h:GD32_EXMC_BANK4]`
- `[gd32f450_memorymap.h:GD32_EXMC_BANK5]`
- `[gd32f450_memorymap.h:GD32_CORTEX_BASE]`
- `[gd32f450_pinmap.h:GPIO_PIN0_OUTPUT]`
- `[gd32f450_pinmap.h:GPIO_PIN1_OUTPUT]`
- `[gd32f450_pinmap.h:GPIO_PIN2_OUTPUT]`
- `[gd32f450_pinmap.h:GPIO_PIN3_OUTPUT]`
- `[gd32f450_pinmap.h:GPIO_PIN4_OUTPUT]`
- `[gd32f450_pinmap.h:GPIO_PIN5_OUTPUT]`
- `[gd32f450_pinmap.h:GPIO_PIN6_OUTPUT]`
- `[gd32f450_pinmap.h:GPIO_PIN7_OUTPUT]`
- `[gd32f450_pinmap.h:GPIO_PIN8_OUTPUT]`
- `[gd32f450_pinmap.h:GPIO_PIN9_OUTPUT]`
- `[gd32f450_pinmap.h:GPIO_PIN10_OUTPUT]`
- `[gd32f450_pinmap.h:GPIO_PIN11_OUTPUT]`
- `[gd32f4xx_dma.h:GD32_DMA0_BASE]`
- `[gd32f4xx_dma.h:GD32_DMA1_BASE]`
- `[gd32f4xx_dma.h:GD32_DMA_INTF0_OFFSET]`
- `[gd32f4xx_dma.h:GD32_DMA_INTF1_OFFSET]`
- `[gd32f4xx_dma.h:GD32_DMA_INTC0_OFFSET]`
- `[gd32f4xx_dma.h:GD32_DMA_INTC1_OFFSET]`

## Invariants
- `[gd32f4xx_memorymap.h:#error]` Compile-time guard: Unsupported GD32F4 memory map
- `[gd32f4xx_pinmap.h:#error]` Compile-time guard: No pinmap file for this GD32 chip

## Side Effects
- None

## Verification
- Run: `make test`
