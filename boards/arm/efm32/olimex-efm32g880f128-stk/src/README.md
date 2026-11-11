# `olimex-efm32g880f128-stk/src` Component (`boards/arm/efm32/olimex-efm32g880f128-stk/src`)

## Overview
Board-level C implementation (`src`) for `olimex-efm32g880f128-stk` (`arm/efm32`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 3 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[efm32g880f128-stk.h:GPIO_BUTTON_1]` Hardware/board configuration macros (`GPIO_BUTTON_1`, `GPIO_BUTTON_2`, `GPIO_BUTTON_3`, `GPIO_BUTTON_4`, `GPIO_IRQ_BUTTON_1`, `GPIO_IRQ_BUTTON_2` (+2 more))
- `[efm32_boot.c:efm32_boardinitialize]` Public function `efm32_boardinitialize()`
- `[efm32_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[efm32_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[efm32_buttons.c:board_buttons]` Public function `board_buttons()`
- `[efm32_buttons.c:board_button_irq]` Public function `board_button_irq()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_BUTTONS`

## Side Effects
- `[efm32_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[efm32_buttons.c:board_button_initialize]` Modifies interrupt controller or critical-section state

## Verification
- Run: `./tools/configure.sh olimex-efm32g880f128-stk:nsh && make`
