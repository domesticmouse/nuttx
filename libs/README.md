# NuttX System Libraries (`libs`)

## Overview
Top-level libraries directory aggregating the NuttX standard C library (`libc`), math library (`libm`), C++ runtime/standard libraries (`libxx`), compiler runtime builtins (`libbuiltin`), fixed/floating-point digital signal processing library (`libdsp`), and NX graphics client/font/widget libraries (`libnx`).

## Subdirectories & Boundaries
- [`libbuiltin`](./libbuiltin/README.md) - Compiler runtime intrinsics (`compiler-rt` and `libgcc`), sanitizer stubs, and coverage profiling hooks.
- [`libc`](./libc/README.md) - Standard C and POSIX library (`libc`) shared between kernel and userspace builds.
- [`libdsp`](./libdsp/README.md) - Fixed-point (`b16_t`) and single-precision (`float`) digital signal processing, motor control (FOC, PID, SVM, observers), and filter library.
- [`libm`](./libm/README.md) - Standard C math library (`<math.h>`, `<complex.h>`, `<fenv.h>`) implementations (`libm` and `newlib` ports).
- [`libnx`](./libnx/README.md) - NX graphics windowing client, font rendering (`nxfonts`), low-level rasterizers (`nxglib`), multi-user client (`nxmu`), and framed toolkit (`nxtk`).
- [`libxx`](./libxx/README.md) - C++ runtime ABI (`libminiabi`) and C++ standard library (`libstdc++`, `uClibc++`) integrations.
