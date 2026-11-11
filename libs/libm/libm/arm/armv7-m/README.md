# armv7-m

## Overview
Provides hardware-accelerated single-precision math routines (`fabsf` and `sqrtf`) for ARMv7-M targets with VFPv4 hardware floating-point support (`vabs.f32` and `vsqrt.f32`).

## Interface
- `arch_fabsf.c:fabsf`
- `arch_sqrtf.c:sqrtf`

## Invariants
- Compiled only when `(__ARM_ARCH >= 7) && (__ARM_FP >= 4)` (`arch_fabsf.c:__ARM_ARCH`, `arch_sqrtf.c:__ARM_FP`).

## Side Effects
- Executes hardware VFP instructions (`vabs.f32`, `vsqrt.f32`), which may update FPU status/exception flags (`FPSCR`) on invalid or negative inputs (`sqrtf`).

## Verification
- Run: `make test`
