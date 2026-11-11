# hardware (`nuttx/arch/risc-v/src/litex/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/risc-v/src/litex/hardware`, providing 7 header file(s) and 0 source file(s) (including `litex_clint.h`, `litex_emac.h`, `litex_memorymap.h`, `litex_plic.h`).

## Interface
- `[litex_clint.h:LITEX_CLINT_MSIP]`
- `[litex_clint.h:LITEX_CLINT_MTIMECMP]`
- `[litex_clint.h:LITEX_CLINT_MTIME]`
- `[litex_clint.h:LITEX_CLINT_LATCH]`
- `[litex_emac.h:ETHMAC_RX_SLOTS]`
- `[litex_emac.h:ETHMAC_TX_SLOTS]`
- `[litex_emac.h:ETHMAC_SLOT_SIZE]`
- `[litex_emac.h:LITEX_ETHMAC_SRAM_WRITER_SLOT_OFFSET]`
- `[litex_emac.h:LITEX_ETHMAC_SRAM_WRITER_LENGTH_OFFSET]`
- `[litex_emac.h:LITEX_ETHMAC_SRAM_WRITER_ERRORS_OFFSET]`
- `[litex_emac.h:LITEX_ETHMAC_SRAM_WRITER_EV_STATUS_OFFSET]`
- `[litex_emac.h:LITEX_ETHMAC_SRAM_WRITER_EV_PENDING_OFFSET]`
- `[litex_emac.h:LITEX_ETHMAC_SRAM_WRITER_EV_ENABLE_OFFSET]`
- `[litex_emac.h:LITEX_ETHMAC_SRAM_READER_START_OFFSET]`
- `[litex_emac.h:LITEX_ETHMAC_SRAM_READER_READY_OFFSET]`
- `[litex_emac.h:LITEX_ETHMAC_SRAM_READER_LEVEL_OFFSET]`
- `[litex_memorymap.h:LITEX_CLINT_BASE]`
- `[litex_memorymap.h:LITEX_PLIC_BASE]`
- `[litex_memorymap.h:LITEX_ETHMAC_BASE]`
- `[litex_memorymap.h:LITEX_ETHPHY_BASE]`
- `[litex_memorymap.h:LITEX_TIMER0_BASE]`
- `[litex_memorymap.h:LITEX_UART0_BASE]`
- `[litex_memorymap.h:LITEX_SDBLOCK2MEM_BASE]`
- `[litex_memorymap.h:LITEX_SDCORE_BASE]`
- `[litex_memorymap.h:LITEX_SDIRQ_BASE]`
- `[litex_memorymap.h:LITEX_SDMEM2BLOCK_BASE]`
- `[litex_memorymap.h:LITEX_SDPHY_BASE]`
- `[litex_memorymap.h:LITEX_CPUTIMER_BASE]`
- `[litex_plic.h:LITEX_PLIC_PRIORITY]`
- `[litex_plic.h:LITEX_PLIC_PENDING1]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
