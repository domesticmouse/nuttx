# `nanopi_m4/src` Component (`boards/arm64/rk3399/nanopi_m4/src`)

## Overview
Board-level C implementation (`src`) for `nanopi_m4` (`arm64/rk3399`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 2 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[nanopi_m4.h]` Board header declarations `nanopi_m4.h`
- `[nanopi_m4_boardinit.c:rk3399_memory_initialize]` Public function `rk3399_memory_initialize()`
- `[nanopi_m4_boardinit.c:rk3399_board_initialize]` Public function `rk3399_board_initialize()`
- `[nanopi_m4_boardinit.c:board_late_initialize]` Public function `board_late_initialize()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ETC_ROMFS`

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh nanopi_m4:nsh && make`
