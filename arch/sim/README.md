# sim (`nuttx/arch/sim`)

## Overview
Architectural grouping for `nuttx/arch/sim` (Simulation Configuration Options; Simulated v4l2m2m support), coordinating 2 component subdirectories (`include`, `src`).

## Subdirectories & Boundaries
- `include`: [./include/README.md](./include/README.md) - Hardware abstraction and architecture package for `include` under `nuttx/arch/sim/include`, providing 8 header file(s) and 0 source file(s) (including `arch.h`, `elf.h`, `inttypes.h`, `irq.h`).
- `src`: [./src/README.md](./src/README.md) - Hardware abstraction and architecture package for `src` under `nuttx/arch/sim/src`, providing 0 header file(s) and 1 source file(s) (including `patch_macho_initsection.py`).

## Interface
- `[Kconfig:CONFIG_HOST_X86_64]`
- `[Kconfig:CONFIG_HOST_X86]`
- `[Kconfig:CONFIG_HOST_ARM]`
- `[Kconfig:CONFIG_HOST_ARM64]`
- `[Kconfig:CONFIG_ARCH_CHIP]`
- `[Kconfig:CONFIG_SIM_TOOLCHAIN_GCC]`
- `[Kconfig:CONFIG_SIM_TOOLCHAIN_CLANG]`
- `[Kconfig:CONFIG_SIM_M32]`
- [./include/README.md](./include/README.md)
- [./src/README.md](./src/README.md)

## Invariants
- None

## Side Effects
- `[patch_macho_initsection.py:open]` Reads or writes local build/configuration files

## Verification
- Run: `make test`
