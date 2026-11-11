# `mizar32a` Board Support Package (`boards/avr/at32uc3/mizar32a`)

## Overview
Board Support Package (BSP) blueprint for `mizar32a` (`avr` / `at32uc3`). Coordinates board initialization, headers, and tooling across `include, src, tools`. Includes build configurations: `nsh`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `mizar32a` (`avr/at32uc3`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:AVR32_FRCOSC]` Hardware/board configuration macros (`AVR32_FRCOSC`, `AVR32_FOSC32`, `AVR32_OSC32STARTUP`, `AVR32_FOSC0`, `AVR32_OSC0STARTUP`, `AVR32_CLOCK_PLL0_OSC0` (+32 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `mizar32a` (`avr/at32uc3`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[mizar32a.h:CONFIG_MIZAR32A_BUTTON1_IRQ]` Hardware/board configuration macros (`CONFIG_MIZAR32A_BUTTON1_IRQ`, `CONFIG_MIZAR32A_BUTTON2_IRQ`, `PINMUX_GPIO_LED1`, `PINMUX_GPIO_BUTTON1`, `GPIO_BUTTON1_IRQ`).
- [`tools`](./tools/README.md) - Board support component `tools` for `mizar32a` (`avr/at32uc3`), containing 1 source/script file(s) (`doisp.sh`). Key symbols: `[doisp.sh]` Shell script entry point `doisp.sh`.
