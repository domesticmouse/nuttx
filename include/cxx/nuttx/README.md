# NuttX C++ `std::abs` Overloads (`include/cxx/nuttx`)

## Overview
Provides the internal C++ helper header (`std_abs.h`) included by `<cstdlib>` and `<cmath>` to undefine any macro `abs` and expose type-safe `std::abs` overloads for `int`, `long`, `long long`, `float`, `double`, and `long double`.

## Interface
- `std_abs.h:abs`, `std_abs.h:labs`, `std_abs.h:llabs`, `std_abs.h:fabsf`, `std_abs.h:fabs`, `std_abs.h:fabsl` - `extern "C"` declarations and inline `std::abs` overloads dispatching to `::labs`, `::llabs`, `::fabsf`, `::fabs`, and `::fabsl`.

## Invariants
- Floating-point `std::abs` overloads in `std_abs.h` are conditionally compiled under `CONFIG_HAVE_FLOAT`, `CONFIG_HAVE_DOUBLE`, and `CONFIG_HAVE_LONG_DOUBLE` to match the target toolchain's FPU/soft-float support.

## Side Effects
- None (pure mathematical value computation and header-level `#undef abs`).

## Verification
- Run: `make test`
