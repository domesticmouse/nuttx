# `nucleo-l073rz/include` Component (`boards/arm/stm32l0/nucleo-l073rz/include`)

## Overview
Board-level public headers (`include`) for `nucleo-l073rz` (`arm/stm32l0`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:stm32_usb_setpullup]` Public declaration `stm32_usb_setpullup()`
- `[board.h:stm32_usb_pullup_enabled]` Public declaration `stm32_usb_pullup_enabled()`
- `[board.h:STM32_BOARD_XTAL]` Hardware/board configuration macros (`STM32_BOARD_XTAL`, `STM32_HSEBYP_ENABLE`, `STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_HSE_FREQUENCY`, `STM32_LSE_FREQUENCY` (+50 more))

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh nucleo-l073rz:nsh && make`
