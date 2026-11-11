# `rv-virt` Board Support Package (`boards/risc-v/qemu-rv/rv-virt`)

## Overview
Board Support Package (BSP) blueprint for `rv-virt` (`risc-v` / `qemu-rv`). Coordinates board initialization, headers, and tooling across `configs, include, kernel, src`. Includes build configurations: `citest`, `citest64`, `elf`, `fb`, `fb64`, `flats` (+31 more).

## Subdirectories & Boundaries
- [`configs`](./configs/README.md) - Intermediate blueprint for `rv-virt/configs` (`risc-v/qemu-rv`), grouping `citest, citest64`.
- [`include`](./include/README.md) - Board-level public headers (`include`) for `rv-virt` (`risc-v/qemu-rv`). Defines board-specific pin mappings, clock frequencies, LED/button definitions, and exported prototypes across 2 header file(s). Key symbols: `[board.h:qemu_rv_boardinitialize]` Public declaration `qemu_rv_boardinitialize()`, `[board.h:BOARD_LED1_BIT]` Hardware/board configuration macros (`BOARD_LED1_BIT`, `BOARD_LED2_BIT`, `BOARD_LED3_BIT`, `LED_STARTED`, `LED_HEAPALLOCATE`, `LED_IRQSENABLED` (+6 more)).
- [`kernel`](./kernel/README.md) - Protected-build userspace/kernel boundary module (`kernel`) for `rv-virt` (`risc-v/qemu-rv`), providing userspace initialization and syscall/gate hooks across 1 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
- [`src`](./src/README.md) - Board-level C implementation (`src`) for `rv-virt` (`risc-v/qemu-rv`). Provides hardware initialization, peripheral bring-up, GPIO/pinmux setup, and driver registration across 5 source file(s). Key symbols: `[Makefile:CSRCS]` Registered build sources in `Makefile`, `[CMakeLists.txt:board]` CMake build target source registration.
