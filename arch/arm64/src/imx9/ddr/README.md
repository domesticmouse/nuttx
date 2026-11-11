# ddr (`nuttx/arch/arm64/src/imx9/ddr`)

## Overview
Hardware abstraction and architecture package for `ddr` under `nuttx/arch/arm64/src/imx9/ddr`, providing 1 header file(s) and 1 source file(s) (including `imx9_ddr_training.h`, `imx9_ddr_training.c`).

## Subdirectories & Boundaries
- `hardware`: [./hardware/README.md](./hardware/README.md) - Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm64/src/imx9/ddr/hardware`, providing 1 header file(s) and 0 source file(s) (including `imx9_ddr_training.h`).

## Interface
- `[imx9_ddr_training.h:imx9_dram_init]`
- `[imx9_ddr_training.h:imx9_ddr_config]`
- `[imx9_ddr_training.c:imx9_check_dfi_init_complete]`
- `[imx9_ddr_training.c:imx9_dram_init]`
- [./hardware/README.md](./hardware/README.md)

## Invariants
- None

## Side Effects
- `[imx9_ddr_training.c:putreg32]` Mutates 32-bit memory-mapped I/O (MMIO) hardware registers (`putreg32`)
- `[imx9_ddr_training.c:modifyreg32]` Performs read-modify-write mutations on 32-bit MMIO hardware registers (`modifyreg32`)
- `[imx9_ddr_training.c:getreg32]` Reads volatile 32-bit memory-mapped hardware status/control registers (`getreg32`)
- `[imx9_ddr_training.c:__asm__]` Executes privileged inline assembly instructions and hardware barrier operations (`__asm__`)

## Verification
- Run: `make test`
