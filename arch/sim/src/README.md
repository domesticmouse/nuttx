# src (`nuttx/arch/sim/src`)

## Overview
Hardware abstraction and architecture package for `src` under `nuttx/arch/sim/src`, providing 0 header file(s) and 1 source file(s) (including `patch_macho_initsection.py`).

## Subdirectories & Boundaries
- `sim`: [./sim/README.md](./sim/README.md) - Hardware abstraction and architecture package for `sim` under `nuttx/arch/sim/src/sim`, providing 12 header file(s) and 54 source file(s) (including `sim_gpiochip.h`, `sim_hostcan.h`, `sim_hosthcisocket.h`, `sim_hostusrsock.h`).

## Interface
- `[patch_macho_initsection.py:main]`
- `[Makefile:CSRCS]`
- `[Makefile:ASRCS]`
- [./sim/README.md](./sim/README.md)

## Invariants
- None

## Side Effects
- `[patch_macho_initsection.py:open]` Reads or writes local build/configuration files

## Verification
- Run: `make test`
