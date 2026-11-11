# arm

## Overview
Groups ARM architecture-specific hardware floating-point overrides for the NuttX built-in math library (`libm`), organized by ARM Cortex-M architecture generation.

## Subdirectories & Boundaries
- armv7-m: [./armv7-m/README.md](./armv7-m/README.md) - ARMv7-M VFPv4 hardware implementations of `fabsf` and `sqrtf`.
- armv8-m: [./armv8-m/README.md](./armv8-m/README.md) - ARMv8-M VFPv5 hardware implementations of single- and double-precision rounding functions (`ceil`, `floor`, `nearbyint`, `rint`, `round`, `trunc`).
