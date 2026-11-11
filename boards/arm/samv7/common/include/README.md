# `common/include` Component (`boards/arm/samv7/common/include`)

## Overview
Board-level public headers (`include`) for `common` (`arm/samv7`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 6 header file(s).

## Interface
- `[board_gpio_enc.h:sam_gpio_enc_init]` Public declaration `sam_gpio_enc_init()`
- `[board_hsmci.h:sam_hsmci_initialize]` Public declaration `sam_hsmci_initialize()`
- `[board_hsmci.h:sam_cardinserted]` Public declaration `sam_cardinserted()`
- `[board_hsmci.h:sam_writeprotected]` Public declaration `sam_writeprotected()`
- `[board_oa_tc6.h:board_oa_tc6_initialize]` Public declaration `board_oa_tc6_initialize()`
- `[board_progmem.h:board_progmem_init]` Public declaration `board_progmem_init()`
- `[board_progmem.h:mtd_partition_s]` Type definition `mtd_partition_s`
- `[board_uart_rxdma_poll.h:board_uart_rxdma_poll_start]` Public declaration `board_uart_rxdma_poll_start()`
- `[board_uart_rxdma_poll.h:board_uart_rxdma_poll_stop]` Public declaration `board_uart_rxdma_poll_stop()`
- `[board_uart_rxdma_poll.h:board_uart_rxdma_poll_init]` Public declaration `board_uart_rxdma_poll_init()`
- `[sam_automount.h:sam_automount_initialize]` Public declaration `sam_automount_initialize()`
- `[sam_automount.h:sam_automount_event]` Public declaration `sam_automount_event()`
- `[sam_automount.h:CONFIG_SAMV7_HSMCI0_AUTOMOUNT_FSTYPE]` Hardware/board configuration macros (`CONFIG_SAMV7_HSMCI0_AUTOMOUNT_FSTYPE`, `CONFIG_SAMV7_HSMCI0_AUTOMOUNT_BLKDEV`, `CONFIG_SAMV7_HSMCI0_AUTOMOUNT_MOUNTPOINT`, `CONFIG_SAMV7_HSMCI0_AUTOMOUNT_DDELAY`, `CONFIG_SAMV7_HSMCI0_AUTOMOUNT_UDELAY`)

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh sim:nsh && make`
