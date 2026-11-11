# `moxa/src` Component (`boards/arm/moxart/moxa/src`)

## Overview
Board-level C implementation (`src`) for `moxa` (`arm/moxart`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 2 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[moxart_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[moxart_reset.c:board_reset]` Public function `board_reset()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_BOARDCTL_RESET`, `CONFIG_ETC_ROMFS`

## Side Effects
- `[moxart_boot.c:board_late_initialize]` Initializes/registers kernel devices or filesystems (`ftmac100_initialize()`)

## Verification
- Run: `./tools/configure.sh moxa:nsh && make`
