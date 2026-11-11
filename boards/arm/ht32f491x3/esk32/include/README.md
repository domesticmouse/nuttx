# `esk32/include` Component (`boards/arm/ht32f491x3/esk32/include`)

## Overview
Board-level public headers (`include`) for `esk32` (`arm/ht32f491x3`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:ht32f491x3_clockconfig]` Public declaration `ht32f491x3_clockconfig()`
- `[board.h:ht32f491x3_boardinitialize]` Public declaration `ht32f491x3_boardinitialize()`
- `[board.h:ht32_pwm_setup]` Public declaration `ht32_pwm_setup()`
- `[board.h:board_userled_initialize]` Public declaration `board_userled_initialize()`
- `[board.h:board_userled]` Public declaration `board_userled()`
- `[board.h:board_userled_all]` Public declaration `board_userled_all()`
- `[board.h:board_late_initialize]` Public declaration `board_late_initialize()`
- `[board.h:BOARD_USART1_GPIO_CLKEN]` Hardware/board configuration macros (`BOARD_USART1_GPIO_CLKEN`, `BOARD_USART1_TX_GPIO_BASE`, `BOARD_USART1_RX_GPIO_BASE`, `BOARD_USART1_TX_PIN`, `BOARD_USART1_RX_PIN`, `BOARD_USART1_TX_AF` (+21 more))

## Invariants
- `[board.h:#error]` Compile-time guard: `esk32 currently exposes PWM only through TMR3`
- `[board.h:#error]` Compile-time guard: `Unsupported CONFIG_HT32F491X3_TMR3_CHANNEL value`

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh esk32:nsh && make`
