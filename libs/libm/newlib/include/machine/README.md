# machine

## Overview
Defines target architecture floating-point endianness (`__IEEE_LITTLE_ENDIAN`, `__IEEE_BIG_ENDIAN`, `__IEEE_BYTES_LITTLE_ENDIAN`), double width (`_DOUBLE_IS_32BITS`), error/exception support (`_SUPPORTS_ERREXCEPT`), and evaluation types (`__DOUBLE_TYPE`, `__FLOAT_TYPE`) for the Newlib `libm` port.

## Interface
- `ieeefp.h:__IEEE_LITTLE_ENDIAN`, `ieeefp.h:__IEEE_BIG_ENDIAN`, `ieeefp.h:__IEEE_BYTES_LITTLE_ENDIAN`, `ieeefp.h:_DOUBLE_IS_32BITS`, `ieeefp.h:_SUPPORTS_ERREXCEPT`, `ieeefp.h:__OBSOLETE_MATH_DEFAULT`, `ieeefp.h:__OBSOLETE_MATH`, `ieeefp.h:__DOUBLE_TYPE`, `ieeefp.h:__FLOAT_TYPE`

## Invariants
- Exactly one of `ieeefp.h:__IEEE_BIG_ENDIAN` or `ieeefp.h:__IEEE_LITTLE_ENDIAN` must be defined for the active target architecture; otherwise preprocessing fails with `#error Endianness not declared!!`.

## Side Effects
- None

## Verification
- Run: `make test`
