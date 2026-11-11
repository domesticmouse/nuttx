# Direct Memory Access (DMA) Subsystem Headers (`include/nuttx/dma`)

## Overview
Defines the generic NuttX Direct Memory Access (`dma`) controller and channel abstraction, supporting single-shot, cyclic, and scatter-gather linked-list (`CONFIG_DMA_LINK`) transfers across memory and peripheral endpoints.

## Interface
- `dma.h:dma_dev_s`, `dma.h:dma_chan_s`, `dma.h:dma_ops_s`, `dma.h:dma_config_s`, `dma.h:dma_callback_t` - DMA controller device, channel handle, channel operation vtable, transfer configuration struct, and completion callback signature.
- `dma.h:dma_link_s`, `dma.h:dma_link_config_s` - Scatter-gather linked-list descriptor structures when `CONFIG_DMA_LINK` is enabled.
- `dma.h:DMA_GET_CHAN`, `dma.h:DMA_PUT_CHAN`, `dma.h:DMA_CONFIG`, `dma.h:DMA_START`, `dma.h:DMA_START_CYCLIC`, `dma.h:DMA_START_LINK`, `dma.h:DMA_PAUSE`, `dma.h:DMA_RESUME`, `dma.h:DMA_STOP`, `dma.h:DMA_RESIDUAL` - Dispatch macros for acquiring/releasing DMA channels and controlling transfers.
- `dma.h:DMA_MEM_TO_MEM`, `dma.h:DMA_MEM_TO_DEV`, `dma.h:DMA_DEV_TO_MEM`, `dma.h:DMA_DEV_TO_DEV` - Transfer direction constants.

## Invariants
- A `dma.h:dma_chan_s` channel must be acquired via `DMA_GET_CHAN` and configured via `DMA_CONFIG` before starting a transfer with `DMA_START`, `DMA_START_CYCLIC`, or `DMA_START_LINK`.
- `dma.h:dma_chan_s.ops` (`dma_ops_s`) must be non-null for all active channels.

## Side Effects
- `dma.h:DMA_START`, `dma.h:DMA_START_CYCLIC`, and `dma.h:DMA_START_LINK` program hardware DMA controller registers and initiate asynchronous bus memory/peripheral reads and writes that invoke `dma_callback_t` in interrupt or workqueue context upon completion.

## Verification
- Run: `make test`
