# C++ Runtime and Standard Library Support (`libs/libxx`)

## Overview
Groups the NuttX C++ ABI runtime and standard library integration layers (`libxx`). Depending on Kconfig selection, this subsystem supplies either a minimal built-in C++ ABI runtime (`libminiabi`) or platform configuration headers for external C++ standard libraries (`libstdc++` and `uClibc++`).

## Subdirectories & Boundaries
- `libminiabi`: [./libminiabi/README.md](./libminiabi/README.md) - Minimal freestanding C++ ABI runtime providing `operator new`/`delete`, `__cxa_guard_*` static initialization guards, `__cxa_pure_virtual`, and Itanium ABI RTTI / `__dynamic_cast`.
- `libstdc++`: [./libstdc++/README.md](./libstdc++/README.md) - GNU ISO C++ Library (`libstdc++` release 13) internal `c++config.h` platform and ABI configuration header for NuttX.
- `uClibc++`: [./uClibc++/README.md](./uClibc++/README.md) - `uClibc++` `system_configuration.h` header mapping NuttX Kconfig options to `__UCLIBCXX_*` feature macros.
