# `sam4s-xplained/src` Component (`boards/arm/sam34/sam4s-xplained/src`)

## Overview
Board-level C implementation (`src`) for `sam4s-xplained` (`arm/sam34`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 6 source file(s).

## Interface
- `[Makefile:CSRCS]` Registered build sources in `Makefile`
- `[CMakeLists.txt:board]` CMake build target source registration
- `[sam4s-xplained.h:sam_sram_initialize]` Public declaration `sam_sram_initialize()`
- `[sam4s-xplained.h:GPIO_D9]` Hardware/board configuration macros (`GPIO_D9`, `GPIO_D10`, `GPIO_BP2`, `IRQ_BP2`, `GPIO_EBI_NLB`)
- `[sam_autoleds.c:board_autoled_initialize]` Public function `board_autoled_initialize()`
- `[sam_autoleds.c:board_autoled_on]` Public function `board_autoled_on()`
- `[sam_autoleds.c:board_autoled_off]` Public function `board_autoled_off()`
- `[sam_boot.c:sam_boardinitialize]` Public function `sam_boardinitialize()`
- `[sam_boot.c:board_late_initialize]` Public function `board_late_initialize()`
- `[sam_buttons.c:board_button_initialize]` Public function `board_button_initialize()`
- `[sam_buttons.c:board_buttons]` Public function `board_buttons()`
- `[sam_buttons.c:board_button_irq]` Public function `board_button_irq()`
- `[sam_sram.c:sam_sram_initialize]` Public function `sam_sram_initialize()`
- `[sam_userleds.c:board_userled_initialize]` Public function `board_userled_initialize()`
- `[sam_userleds.c:board_userled]` Public function `board_userled()`
- `[sam_userleds.c:board_userled_all]` Public function `board_userled_all()`

## Invariants
- `[Makefile:CONFIG_*]` Conditional compilation gated by `CONFIG_ARCH_BUTTONS`, `CONFIG_ARCH_LEDS`, `CONFIG_SAM34_EXTSRAM0`
- `[sam_buttons.c:board_button_initialize]` Validates preconditions and returns `-EINVAL` on failure

## Side Effects
- `[sam_autoleds.c:board_autoled_initialize]` Configures or drives hardware GPIO pins
- `[sam_boot.c:sam_boardinitialize]` Initializes/registers kernel devices or filesystems (`board_autoled_initialize()`, `sam_sram_initialize()`)
- `[sam_buttons.c:board_button_initialize]` Configures or drives hardware GPIO pins
- `[sam_buttons.c:board_button_initialize]` Modifies interrupt controller or critical-section state
- `[sam_sram.c:sam_sram_initialize]` Performs memory-mapped hardware register writes (`putreg*`/`modifyreg*`)
- `[sam_sram.c:sam_sram_initialize]` Configures or drives hardware GPIO pins
- `[sam_userleds.c:board_userled_initialize]` Configures or drives hardware GPIO pins

## Verification
- Run: `./tools/configure.sh sam4s-xplained:nsh && make`
