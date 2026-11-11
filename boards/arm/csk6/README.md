# `csk6` Family Boards (`boards/arm/csk6`)

## Overview
Intermediate blueprint grouping board support packages and shared board drivers for the `csk6` SoC/MCU family under the `arm` architecture (2 subdirectories).

## Subdirectories & Boundaries
- [`csk6011a-nano`](./csk6011a-nano/README.md) - Board Support Package (BSP) blueprint for `csk6011a-nano` (`arm` / `csk6`). Coordinates board initialization, headers, and tooling across `include, src`. Includes build configurations: `nsh`.
- [`tools`](./tools/README.md) - Component package providing `tools` utilities and board support files (`patch_header.py`) for the `csk6` family (`arm` architecture). Key symbols: `[patch_header.py:DEFAULT_INPUT_FILE]` Default input binary filename `"nuttx.bin"`, `[patch_header.py:DEFAULT_OUTPUT_FILE]` Default output binary filename `"nuttx.bin"`.
