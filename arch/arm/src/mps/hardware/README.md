# hardware (`nuttx/arch/arm/src/mps/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/mps/hardware`, providing 1 header file(s) and 0 source file(s) (including `mps_memorymap.h`).

## Interface
- `[mps_memorymap.h:MPS_ITCM_START]`
- `[mps_memorymap.h:MPS_ITCM_SIZE]`
- `[mps_memorymap.h:MPS_SRAM1_START]`
- `[mps_memorymap.h:MPS_SRAM1_SIZE]`
- `[mps_memorymap.h:MPS_SRAM2_START]`
- `[mps_memorymap.h:MPS_SRAM2_SIZE]`
- `[mps_memorymap.h:MPS_EXTMEM_START]`
- `[mps_memorymap.h:MPS_EXTMEM_SIZE]`
- `[mps_memorymap.h:MPS_PSRAM_START]`
- `[mps_memorymap.h:MPS_PSRAM_SIZE]`
- `[mps_memorymap.h:PRIMARY_RAM_START]`
- `[mps_memorymap.h:PRIMARY_RAM_SIZE]`

## Invariants
- `[mps_memorymap.h:#error]` Compile-time guard: Unrecognized Arm MPS2 and MPS3 architecture

## Side Effects
- None

## Verification
- Run: `make test`
