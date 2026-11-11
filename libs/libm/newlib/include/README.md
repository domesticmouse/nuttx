# include

## Overview
Provides public C99/POSIX mathematical headers (`math.h`, `complex.h`, `tgmath.h`, and `ieeefp.h`) for the Newlib `libm` integration in NuttX, declaring real and complex math prototypes, IEEE-754 bitfield unions, floating-point classification macros, and type-generic math dispatch macros.

## Interface
- `math.h:float_t`, `math.h:double_t`, `math.h:fpclassify`, `math.h:isfinite`, `math.h:isinf`, `math.h:isnan`, `math.h:isnormal`, `math.h:signbit`, `math.h:math_errhandling`, `math.h:signgam`, `math.h:_tls_gamma_signgam`, plus standard C99 `double`, `float`, and `long double` math function declarations (`sin`, `cos`, `tan`, `exp`, `log`, `pow`, `sqrt`, `fma`, `lgamma_r`, `sincos`, etc.)
- `complex.h:complex`, `complex.h:_Complex_I`, `complex.h:I`, plus C99 complex declarations (`cacos`, `casin`, `catan`, `ccos`, `csin`, `ctan`, `cexp`, `clog`, `cabs`, `cpow`, `csqrt`, `carg`, `cimag`, `conj`, `cproj`, `creal`, `clog10`, and `f`/`l` variants)
- `tgmath.h:__tg_impl_simple`, `tgmath.h:__tg_impl_full`, and type-generic macros for real and complex functions
- `ieeefp.h:__ieee_double_shape_type`, `ieeefp.h:__ieee_float_shape_type`, `ieeefp.h:ieee_ext_u`, `ieeefp.h:fp_rnd`, `ieeefp.h:fp_except`, `ieeefp.h:fp_rdi`, `ieeefp.h:fpgetround`, `ieeefp.h:fpsetround`, `ieeefp.h:fpgetmask`, `ieeefp.h:fpsetmask`, `ieeefp.h:fpgetsticky`, `ieeefp.h:fpsetsticky`
- Subdirectories:
  - `./machine/README.md` - Target-specific IEEE-754 endianness and floating-point feature macros.

## Invariants
- `tgmath.h` requires GCC >= 3.1 (`tgmath.h:__GNUC_PREREQ`) for `__builtin_types_compatible_p` and `__builtin_choose_expr`.
- `math.h:_LDBL_EQ_DBL` is defined to `1` so `long double` declarations map to `double` equivalents where extended precision is not distinct.

## Side Effects
- `math.h:_REENT_SIGNGAM` references thread-local `math.h:_tls_gamma_signgam` for reentrant gamma sign storage.

## Verification
- Run: `make test`
