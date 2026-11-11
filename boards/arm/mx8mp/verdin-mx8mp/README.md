# `verdin-mx8mp` Board Support Package (`boards/arm/mx8mp/verdin-mx8mp`)

## Overview
Board Support Package (BSP) blueprint for `verdin-mx8mp` (`arm` / `mx8mp`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`, `rpmsg`.

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `verdin-mx8mp` (`arm/mx8mp`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:IOMUX_CONSOLE_UART_RX]` Hardware/board configuration macros (`IOMUX_CONSOLE_UART_RX`, `IOMUX_CONSOLE_UART_TX`, `BOARD_LED_1`, `BOARD_LED_2`, `BOARD_LED_3`, `BOARD_LED_4` (+17 more)).
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `verdin-mx8mp` (`arm/mx8mp`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 11 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
