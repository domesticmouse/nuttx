# NuttX Video Subsystem (`video`)

## Overview
Top-level video subsystem build glue (`Makefile`, `CMakeLists.txt`, `Kconfig`) and an empty translation unit (`dummy.c`) used to prevent empty archive creation errors when no video sources are enabled, plus the `videomode` display timing and EDID library.

## Interface
- `[Kconfig:CONFIG_VIDEO]`
- `[CMakeLists.txt:video]`
- `[Makefile:BIN]`
- [`videomode`](./videomode/README.md) - Display timing, DMT video mode lookup/sorting, VESA GTF, and 128-byte EDID parser library.

## Invariants
- If `ASRCS` and `CSRCS` are both empty, `CSRCS` defaults to `dummy.c` so `libvideo.a` has at least one object file `[Makefile:CSRCS]`.

## Side Effects
- None

## Verification
- Run: `make test`
