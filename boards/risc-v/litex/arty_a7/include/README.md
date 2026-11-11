# `arty_a7/include` Component (`boards/risc-v/litex/arty_a7/include`)

## Overview
Board-level public headers (`include`) for `arty_a7` (`risc-v/litex`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 4 header file(s).

## Interface
- `[board.h:litex_boardinitialize]` Public declaration `litex_boardinitialize()`
- `[board_memorymap.h:KFLASH_START]` Hardware/board configuration macros (`KFLASH_START`, `KFLASH_SIZE`, `KSRAM_START`, `KSRAM_SIZE`, `KSRAM_END`, `PGPOOL_START` (+6 more))
- `[vexii_irq.h:LITEX_IRQ_UART0]` Hardware/board configuration macros (`LITEX_IRQ_UART0`, `LITEX_IRQ_TIMER0`, `LITEX_IRQ_ETHMAC`, `LITEX_IRQ_GPIO_BASE`, `LITEX_IRQ_GPIO_LENGTH`, `LITEX_IRQ_LAST` (+4 more))
- `[vexii_memorymap.h:LITEX_CLINT_BASE]` Hardware/board configuration macros (`LITEX_CLINT_BASE`, `LITEX_PLIC_BASE`, `LITEX_UART0_BASE`, `LITEX_TIMER0_BASE`, `LITEX_ETHMAC_BASE`, `LITEX_ETHPHY_BASE` (+5 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh arty_a7:nsh && make`
