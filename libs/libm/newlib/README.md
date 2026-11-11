# newlib

## Overview
Integrates the Newlib `libm` mathematical library into NuttX, providing the `sincosl` wrapper, build rules/patches for external Newlib sources, and Newlib math headers.

## Interface
- `sincosl.c:sincosl`
- Subdirectories:
  - `./include/README.md` - Public `math.h`, `complex.h`, `tgmath.h`, and `ieeefp.h` headers for Newlib `libm`.

## Invariants
- `sincosl.c:sincosl` must be compiled with `nooptimiziation_function` (`-O0`) so the compiler does not lower `sinl(x)` and `cosl(x)` back into an infinite recursive call to `sincosl`.

## Side Effects
- `sincosl.c:sincosl` writes computed sine and cosine values to caller-supplied `long double *s` and `long double *c` pointers.

## Verification
- Run: `make test`
