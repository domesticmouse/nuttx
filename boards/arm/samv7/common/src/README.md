# `common/src` Component (`boards/arm/samv7/common/src`)

## Overview
Board-level C implementation (`src`) for `common` (`arm/samv7`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 7 source file(s).

## Interface
- `[Make.defs:CSRCS]` Registered build sources in `Make.defs`
- `[sam_automount.c:sam_automount_initialize]` Public function `sam_automount_initialize()`
- `[sam_automount.c:sam_automount_event]` Public function `sam_automount_event()`
- `[sam_boot_image.c:board_boot_image]` Public function `board_boot_image()`
- `[sam_gpio_enc.c:sam_gpio_enc_init]` Public function `sam_gpio_enc_init()`
- `[sam_hsmci.c:sam_hsmci_initialize]` Public function `sam_hsmci_initialize()`
- `[sam_hsmci.c:sam_cardinserted]` Public function `sam_cardinserted()`
- `[sam_hsmci.c:sam_writeprotected]` Public function `sam_writeprotected()`
- `[sam_progmem.c:board_progmem_init]` Public function `board_progmem_init()`
- `[sam_reset.c:board_reset_cause]` Public function `board_reset_cause()`
- `[sam_reset.c:board_reset]` Public function `board_reset()`
- `[sam_uart_rxdma_poll.c:board_uart_rxdma_poll_start]` Public function `board_uart_rxdma_poll_start()`
- `[sam_uart_rxdma_poll.c:board_uart_rxdma_poll_stop]` Public function `board_uart_rxdma_poll_stop()`
- `[sam_uart_rxdma_poll.c:board_uart_rxdma_poll_init]` Public function `board_uart_rxdma_poll_init()`

## Invariants
- `[Make.defs:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH`, `CONFIG_ARCH_BOARD_COMMON`, `CONFIG_BOARDCTL_BOOT_IMAGE`, `CONFIG_FS_AUTOMOUNTER`, `CONFIG_MTD_PROGMEM`, `CONFIG_SAMV7_GPIO_ENC` (+3 more)
- `[sam_automount.c:DEBUGASSERT]` Requires `config && config->state`
- `[sam_gpio_enc.c:sam_gpio_enc_init]` Validates preconditions and returns `-ENOTTY` on failure
- `[sam_hsmci.c:sam_hsmci_initialize]` Validates preconditions and returns `-EINVAL`, `-ENODEV` on failure
- `[sam_progmem.c:ASSERT]` Requires `(mtd_offset + mtd_size) <= up_progmem_neraseblocks(`
- `[sam_progmem.c:ASSERT]` Requires `(mtd_offset % up_progmem_pagesize(0)) == 0`
- `[sam_progmem.c:ASSERT]` Requires `(mtd_size % up_progmem_pagesize(0)) == 0`
- `[sam_uart_rxdma_poll.c:DEBUGASSERT]` Requires `div > 0 && div <= fdiv`

## Side Effects
- `[sam_automount.c:sam_automount_initialize]` Initializes/registers kernel devices or filesystems (`automount_initialize()`)
- `[sam_automount.c:sam_automount_initialize]` Modifies interrupt controller or critical-section state
- `[sam_boot_image.c:board_boot_image]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[sam_gpio_enc.c:sam_gpio_enc_init]` Configures or drives hardware GPIO pins
- `[sam_gpio_enc.c:sam_gpio_enc_init]` Initializes/registers kernel devices or filesystems (`qe_register()`)
- `[sam_gpio_enc.c:sam_gpio_enc_init]` Modifies interrupt controller or critical-section state
- `[sam_hsmci.c:sam_hsmci_initialize]` Configures or drives hardware GPIO pins
- `[sam_hsmci.c:sam_hsmci_initialize]` Initializes/registers kernel devices or filesystems (`sdio_initialize()`)
- `[sam_hsmci.c:sam_hsmci_initialize]` Modifies interrupt controller or critical-section state
- `[sam_progmem.c:board_progmem_init]` Initializes/registers kernel devices or filesystems (`progmem_initialize()`, `sam_progmem_initialize()`)

## Verification
- Run: `./tools/configure.sh sim:nsh && make`
