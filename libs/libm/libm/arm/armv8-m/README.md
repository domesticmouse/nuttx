# armv8-m

## Overview
Provides hardware-accelerated single-precision (`float`) and double-precision (`double`) rounding and truncation math routines (`ceil`, `floor`, `nearbyint`, `rint`, `round`, `trunc`) for ARMv8-M targets using VFPv5 instructions (`vrintp`, `vrintm`, `vrintr`, `vrintx`, `vrinta`, `vrintz`).

## Interface
- `arch_ceil.c:ceil`, `arch_ceilf.c:ceilf`
- `arch_floor.c:floor`, `arch_floorf.c:floorf`
- `arch_nearbyint.c:nearbyint`, `arch_nearbyintf.c:nearbyintf`
- `arch_rint.c:rint`, `arch_rintf.c:rintf`
- `arch_round.c:round`, `arch_roundf.c:roundf`
- `arch_trunc.c:trunc`, `arch_truncf.c:truncf`

## Invariants
- Single-precision implementations require `__ARM_ARCH >= 8 && !defined(__SOFTFP__)` (`arch_ceilf.c:__ARM_ARCH`), and double-precision implementations additionally require `(__ARM_FP & 0x8)` (`arch_ceil.c:__ARM_FP`).

## Side Effects
- Executes inline VFP instructions (`vrintp`, `vrintm`, `vrintr`, `vrintx`, `vrinta`, `vrintz`), reading the active rounding mode and potentially setting inexact or invalid exception bits in `FPSCR` (`arch_rint.c:rint`, `arch_rintf.c:rintf`).

## Verification
- Run: `make test`
