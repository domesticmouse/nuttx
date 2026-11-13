# `nucleo-g491re/include` Component (`boards/arm/stm32g4/nucleo-g491re/include`)

## Overview
Board-level public headers (`include`) for `nucleo-g491re` (`arm/stm32g4`). Defines board-specific clock tree frequencies (16 MHz HSI multiplied to 170 MHz SYSCLK/HCLK/PCLK1/PCLK2 via PLL), LPUART1/USART3 pin mappings, user LED (`LD2` on `PA5`), and user button (`B1` on `PC13`) definitions across 1 header file (`board.h`).

## Interface
- `[board.h:STM32_HSI_FREQUENCY]` Hardware/board clock and PLL configuration macros (`STM32_HSI_FREQUENCY`, `STM32_LSI_FREQUENCY`, `STM32_PLLCFGR_PLLSRC`, `STM32_PLLCFGR_PLLCFG`, `STM32_PLLCFGR_PLLN`, `STM32_PLLCFGR_PLLM`, `STM32_PLLCFGR_PLLP`, `STM32_PLLCFGR_PLLQ`, `STM32_PLLCFGR_PLLR`, `STM32_SYSCLK_FREQUENCY`, `STM32_HCLK_FREQUENCY`, `STM32_PCLK1_FREQUENCY`, `STM32_PCLK2_FREQUENCY`)
- `[board.h:GPIO_LPUART1_TX]` UART, LED, and button pin/state macros (`GPIO_LPUART1_TX`, `GPIO_LPUART1_RX`, `GPIO_USART3_TX`, `GPIO_USART3_RX`, `BOARD_LED1`, `BOARD_NLEDS`, `LED_STARTED`, `LED_PANIC`, `BUTTON_USER`, `NUM_BUTTONS`)

## Invariants
- `[board.h:STM32_VCO_FREQUENCY]` VCO frequency (`340 MHz`) must remain within `64 MHz..344 MHz` and `PLLP`/`PLLQ`/`PLLR` clocks must not exceed `170 MHz`.

## Side Effects
- None

## Verification
- Run: `./tools/configure.sh nucleo-g491re:nsh && make`
