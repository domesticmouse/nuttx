# `cloudctrl/include` Component (`boards/arm/stm32f1/cloudctrl/include`)

## Overview
Board-level public headers (`include`) for `cloudctrl` (`arm/stm32f1`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s).

## Interface
- `[board.h:stm32_lcdclear]` Public declaration `stm32_lcdclear()`
- `[board.h:up_relaysinit]` Public declaration `up_relaysinit()`
- `[board.h:relays_setstat]` Public declaration `relays_setstat()`
- `[board.h:relays_getstat]` Public declaration `relays_getstat()`
- `[board.h:relays_setstats]` Public declaration `relays_setstats()`
- `[board.h:relays_getstats]` Public declaration `relays_getstats()`
- `[board.h:relays_onoff]` Public declaration `relays_onoff()`
- `[board.h:relays_onoffs]` Public declaration `relays_onoffs()`
- `[board.h:relays_resetmode]` Public declaration `relays_resetmode()`
- `[board.h:relays_powermode]` Public declaration `relays_powermode()`
- `[board.h:relays_resetmodes]` Public declaration `relays_resetmodes()`
- `[board.h:relays_powermodes]` Public declaration `relays_powermodes()`
- `[board.h:stm32_getchipid]` Public declaration `stm32_getchipid()`
- `[board.h:stm32_getchipid_string]` Public declaration `stm32_getchipid_string()`
- `[board.h:STM32_BOARD_XTAL]` Hardware/board configuration macros (`STM32_BOARD_XTAL`, `STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_HSE_FREQUENCY`, `STM32_LSE_FREQUENCY`, `STM32_PLL_PREDIV2` (+86 more))

## Invariants
- `[board.h:#error]` Compile-time guard: `STM32 Ethernet requires CONFIG_STM32_ETH_REMAP`
- `[board.h:#error]` Compile-time guard: `STM32 Ethernet requires CONFIG_STM32_RMII`

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh cloudctrl:nsh && make`
