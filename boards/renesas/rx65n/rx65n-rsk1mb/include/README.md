# `rx65n-rsk1mb/include` Component (`boards/renesas/rx65n/rx65n-rsk1mb/include`)

## Overview
Board-level public headers (`include`) for `rx65n-rsk1mb` (`renesas/rx65n`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s).

## Interface
- `[board.h:RX_FCLK]` Hardware/board configuration macros (`RX_FCLK`, `RX_ICLK`, `RX_PCLKA`, `RX_PCLKB`, `RX_PCLKC`, `RX_PCLKD` (+13 more))
- `[rx65n_gpio.h:sci_port_create]` Public declaration `sci_port_create()`
- `[rx65n_gpio.h:led_port_create]` Public declaration `led_port_create()`
- `[rx65n_gpio.h:r_ether_pheriperal_enable]` Public declaration `r_ether_pheriperal_enable()`
- `[rx65n_gpio.h:sci2_init_port]` Public declaration `sci2_init_port()`

## Invariants
- `[board.h:#error]` Compile-time guard: `Please definition RX_RESONATOR in board.h`
- `[board.h:#error]` Compile-time guard: `LEDs are not defined.`

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh rx65n-rsk1mb:nsh && make`
