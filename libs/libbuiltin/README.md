# libbuiltin

## Overview
Groups compiler builtin and instrumentation runtime libraries for NuttX, providing LLVM `compiler-rt` and GCC `libgcc` profiling and code coverage support (`gcov`, `gprof`, and `llvm-profdata`).

## Subdirectories & Boundaries
- compiler-rt: [./compiler-rt/README.md](./compiler-rt/README.md) - LLVM `compiler-rt` instrumentation profiling and raw coverage dump runtime.
- libgcc: [./libgcc/README.md](./libgcc/README.md) - GCC `gcov` coverage runtime and `gmon`/`gprof` call-graph and histogram profiling runtime.
