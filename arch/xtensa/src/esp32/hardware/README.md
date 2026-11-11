# hardware (`nuttx/arch/xtensa/src/esp32/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/xtensa/src/esp32/hardware`, providing 26 header file(s) and 0 source file(s) (including `esp32_aes.h`, `esp32_apb_ctrl.h`, `esp32_dma.h`, `esp32_dport.h`).

## Interface
- `[esp32_aes.h:AES_START_REG]`
- `[esp32_aes.h:AES_IDLE_REG]`
- `[esp32_aes.h:AES_MODE_REG]`
- `[esp32_aes.h:AES_KEY_BASE]`
- `[esp32_aes.h:AES_TEXT_BASE]`
- `[esp32_aes.h:AES_ENDIAN]`
- `[esp32_aes.h:AES_START_OPT]`
- `[esp32_aes.h:AES_IDLE_STATE]`
- `[esp32_aes.h:AES_MODE_DECRYPT]`
- `[esp32_apb_ctrl.h:APB_CTRL_SYSCLK_CONF_REG]`
- `[esp32_apb_ctrl.h:APB_CTRL_QUICK_CLK_CHNG]`
- `[esp32_apb_ctrl.h:APB_CTRL_QUICK_CLK_CHNG_M]`
- `[esp32_apb_ctrl.h:APB_CTRL_QUICK_CLK_CHNG_V]`
- `[esp32_apb_ctrl.h:APB_CTRL_QUICK_CLK_CHNG_S]`
- `[esp32_apb_ctrl.h:APB_CTRL_RST_TICK_CNT]`
- `[esp32_apb_ctrl.h:APB_CTRL_RST_TICK_CNT_M]`
- `[esp32_apb_ctrl.h:APB_CTRL_RST_TICK_CNT_V]`
- `[esp32_apb_ctrl.h:APB_CTRL_RST_TICK_CNT_S]`
- `[esp32_apb_ctrl.h:APB_CTRL_CLK_EN]`
- `[esp32_apb_ctrl.h:APB_CTRL_CLK_EN_M]`
- `[esp32_apb_ctrl.h:APB_CTRL_CLK_EN_V]`
- `[esp32_dma.h:DMA_CTRL_OWN]`
- `[esp32_dma.h:DMA_CTRL_EOF]`
- `[esp32_dma.h:DMA_CTRL_SOSF]`
- `[esp32_dma.h:DMA_CTRL_OFFSET_S]`
- `[esp32_dma.h:DMA_CTRL_OFFSET_V]`
- `[esp32_dma.h:DMA_CTRL_DATALEN_S]`
- `[esp32_dma.h:DMA_CTRL_DATALEN_V]`
- `[esp32_dma.h:DMA_CTRL_BUFLEN_S]`
- `[esp32_dma.h:DMA_CTRL_BUFLEN_V]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
