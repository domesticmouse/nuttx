# `rx65n-rsk1mb/src` Component (`boards/renesas/rx65n/rx65n-rsk1mb/src`)

## Overview
Board-level C implementation (`src`) for `rx65n-rsk1mb` (`renesas/rx65n`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 2 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[rx65n_gpio.c:led_port_create]` Public function `led_port_create()`
- `[rx65n_gpio.c:sci_port_create]` Public function `sci_port_create()`
- `[rx65n_gpio.c:r_ether_pheriperal_enable]` Public function `r_ether_pheriperal_enable()`
- `[rx65n_gpio.c:sci2_init_port]` Public function `sci2_init_port()`
- `[rx65n_main.c:board_autoled1_on]` Public function `board_autoled1_on()`
- `[rx65n_main.c:board_autoled2_on]` Public function `board_autoled2_on()`
- `[rx65n_main.c:board_autoled_on]` Public function `board_autoled_on()`
- `[rx65n_main.c:board_autoled1_off]` Public function `board_autoled1_off()`
- `[rx65n_main.c:board_autoled2_off]` Public function `board_autoled2_off()`
- `[rx65n_main.c:board_autoled_off]` Public function `board_autoled_off()`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh rx65n-rsk1mb:nsh && make`
