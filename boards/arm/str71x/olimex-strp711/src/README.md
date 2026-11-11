# `olimex-strp711/src` Component (`boards/arm/str71x/olimex-strp711/src`)

## Overview
Board-level C implementation (`src`) for `olimex-strp711` (`arm/str71x`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[str71_boardinit.c:board_late_initialize]` Public function `board_late_initialize()`
- `[str71_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[str71_buttons.c:board_buttons]` Public function `board_buttons()`
- `[str71_enc28j60.c:arm_netinitialize]` Public function `arm_netinitialize()`
- `[str71_leds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[str71_leds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[str71_leds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[str71_spi.c:str71_spibus_initialize]` Public function `str71_spibus_initialize()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ENC28J60`
- `[str71_enc28j60.c:#error]` Compile-time guard: `Need CONFIG_STR71X_BSPI0 in the configuration`
- `[str71_enc28j60.c:#error]` Compile-time guard: `Need CONFIG_STR71X_XTI in the configuration`
- `[str71_leds.c:#error]` Compile-time guard: `LEDs require GPIO1`
- `[str71_spi.c:DEBUGASSERT]` Requires `priv && priv->spibase`
- `[str71_spi.c:#error]` Compile-time guard: `Invalid RX FIFO depth setting`
- `[str71_spi.c:#error]` Compile-time guard: `Invalid TX FIFO depth setting`

## Side Effects
- `[str71_boardinit.c:board_late_initialize]` Initializes/registers kernel devices or filesystems (`str71_spibus_initialize()`)
- `[str71_buttons.c:board_button_initialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[str71_enc28j60.c:arm_netinitialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[str71_enc28j60.c:arm_netinitialize]` Initializes/registers kernel devices or filesystems (`enc_initialize()`, `str71_spibus_initialize()`)
- `[str71_enc28j60.c:arm_netinitialize]` Modifies interrupt controller or critical-section state
- `[str71_leds.c:board_autoled_initialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[str71_spi.c:str71_spibus_initialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[str71_spi.c:str71_spibus_initialize]` Modifies interrupt controller or critical-section state

## Verification
- Run: `./tools/configure.sh olimex-strp711:nsh && make`
