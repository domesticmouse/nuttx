# libm

## Overview
Top-level mathematical library (`libm`) directory for NuttX, grouping the native NuttX math implementation (`libm`) and the Newlib math library integration (`newlib`).

## Subdirectories & Boundaries
- libm: [./libm/README.md](./libm/README.md) - Native NuttX standard C math library and architecture-specific FPU implementations (ARM, RISC-V).
- newlib: [./newlib/README.md](./newlib/README.md) - Newlib `libm` integration, `sincosl` wrapper, and standard C99/IEEE-754 math headers.
