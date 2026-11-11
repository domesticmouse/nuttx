# `maix-bit` Board Support Package (`boards/risc-v/k210/maix-bit`)

## Overview
Board Support Package (BSP) blueprint for `maix-bit` (`risc-v` / `k210`). Coordinates board initialization, headers, and tooling across `include, kernel, src`. Includes build configurations: `elf`, `knsh`, `knsh_smp`, `kostest`, `module`, `nsh` (+3 more).

## Subdirectories & Boundaries
- [`include`](./include/README.md) - Board-level public headers (`include`) for `maix-bit` (`risc-v/k210`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 1 header file(s). Key symbols: `[board.h:k210_boardinitialize]` Public declaration `k210_boardinitialize()`, `[board.h:BOARD_LED_PAD]` Hardware/board configuration macros (`BOARD_LED_PAD`, `BOARD_LED_IO_FUNC`, `BOARD_LED_IO`, `LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED` (+10 more)).
- [`kernel`](./kernel/README.md) - Protected-build userspace/kernel boundary module (`kernel`) for `maix-bit` (`risc-v/k210`), providing userspace initialization and syscall/gate hooks across 1 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[k210_userspace.c:g_userspace_data]` Module symbol `g_userspace_data`.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `maix-bit` (`risc-v/k210`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
