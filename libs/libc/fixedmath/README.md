# Fixed-Point Mathematics (`libs/libc/fixedmath`)

## Overview
Implements 16.16 (`b16_t`, `ub16_t`) and 8.8 (`ub8_t`) fixed-point mathematical functions declared in `<fixedmath.h>`, including trigonometric functions (`b16sin`, `b16cos`, `b16atan2`) and iterative Newton-Raphson square root calculations (`ub32sqrtub16`, `ub16sqrtub8`).

## Interface
- `[lib_b16sin.c:b16sin]` - Computes the sine of radian angle `rad` (`b16_t`) using range reduction to `[-pi/2, pi/2]` and a polynomial approximation.
- `[lib_b16cos.c:b16cos]` - Macro/wrapper in `<fixedmath.h>` and helper computing the cosine of `rad` (`b16_t`).
- `[lib_b16atan2.c:b16atan2]` - Computes the four-quadrant inverse tangent `atan2(y, x)` in `b16_t` radians for `b16_t` inputs `y` and `x`.
- `[lib_ubsqrt.c:ub32sqrtub16]` - Computes the unsigned 16.16 fixed-point square root (`ub16_t`) of an unsigned 32.32 fixed-point input (`ub32_t`).
- `[lib_ubsqrt.c:ub16sqrtub8]` - Computes the unsigned 8.8 fixed-point square root (`ub8_t`) of an unsigned 16.16 fixed-point input (`ub16_t`).

## Invariants
- Pure arithmetic functions with no global state.
- `[lib_ubsqrt.c:ub32sqrtub16]` and `[lib_ubsqrt.c:ub16sqrtub8]` return `0` for `0` input and clamp initial guesses at `UINT64_MAX` / `UINT32_MAX` to prevent integer overflow during iteration.

## Side Effects
- None

## Verification
- Run: `make test`
