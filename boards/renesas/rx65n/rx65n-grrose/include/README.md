# `rx65n-grrose/include` Component (`boards/renesas/rx65n/rx65n-grrose/include`)

## Overview
Board-level public headers (`include`) for `rx65n-grrose` (`renesas/rx65n`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s).

## Interface
- `[board.h:RX_FCLK]` Hardware/board configuration macros (`RX_FCLK`, `RX_ICLK`, `RX_PCLKA`, `RX_PCLKB`, `RX_PCLKC`, `RX_PCLKD` (+15 more))
- `[rx65n_gpio.h:sci_port_create]` Public declaration `sci_port_create()`
- `[rx65n_gpio.h:led_port_create]` Public declaration `led_port_create()`
- `[rx65n_gpio.h:r_ether_pheriperal_enable]` Public declaration `r_ether_pheriperal_enable()`
- `[rx65n_gpio.h:r_usbdev_port_enable]` Public declaration `r_usbdev_port_enable()`
- `[rx65n_gpio.h:sci0_init_port]` Public declaration `sci0_init_port()`
- `[rx65n_gpio.h:sci1_init_port]` Public declaration `sci1_init_port()`
- `[rx65n_gpio.h:sci2_init_port]` Public declaration `sci2_init_port()`
- `[rx65n_gpio.h:sci3_init_port]` Public declaration `sci3_init_port()`
- `[rx65n_gpio.h:sci5_init_port]` Public declaration `sci5_init_port()`
- `[rx65n_gpio.h:sci6_init_port]` Public declaration `sci6_init_port()`
- `[rx65n_gpio.h:sci8_init_port]` Public declaration `sci8_init_port()`
- `[rx65n_gpio.h:riic0_init_port]` Public declaration `riic0_init_port()`
- `[rx65n_gpio.h:riic1_init_port]` Public declaration `riic1_init_port()`
- `[rx65n_gpio.h:riic2_init_port]` Public declaration `riic2_init_port()`
- `[rx65n_gpio.h:PHY_STS_REG]` Hardware/board configuration macros (`PHY_STS_REG`, `PHY_STS_REG_AUTO_NEG`, `PHY_STS_READ_REG`, `PHY_STS_BIT_MASK`, `PHY_STS_SHIFT_COUNT`, `PHY_STS_REG_LINK` (+6 more))

## Invariants
- `[board.h:#error]` Compile-time guard: `Please definition RX_RESONATOR in board.h`
- `[board.h:#error]` Compile-time guard: `No Selection for PORT definition in rx65n_port.c`

## Side Effects
- `[rx65n_gpio.h:sci_port_create]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh rx65n-grrose:nsh && make`
