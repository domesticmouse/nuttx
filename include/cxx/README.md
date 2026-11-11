# NuttX C++ Standard Library C-Header Wrappers (`include/cxx`)

## Overview
Provides lightweight C++ standard library `<c*>` wrapper headers (`<cmath>`, `<cstdlib>`, `<cstdio>`, `<cstring>`, `<cstdint>`, `<cstddef>`, `<ctime>`, `<cwchar>`, `<cwctype>`, `<cctype>`, `<cerrno>`, `<csignal>`, `<clocale>`, `<climits>`, `<cassert>`, `<cstdbool>`, `<cstdarg>`, `<cinttypes>`) that include the corresponding NuttX C headers and import their types and functions into `namespace std`.

## Interface
- `cmath:float_t`, `cmath:double_t`, `cmath:signbit`, `cmath:fpclassify`, `cmath:isfinite`, `cmath:isinf`, `cmath:isnan`, `cmath:nextafter` - `namespace std` floating-point classification overloads and math function imports (`sin`, `cos`, `sqrt`, `pow`, `fabs`, etc.).
- `cstdlib:malloc`, `cstdlib:free`, `cstdlib:realloc`, `cstdlib:calloc`, `cstdlib:abort`, `cstdlib:exit`, `cstdlib:strtol`, `cstdlib:qsort`, `cstdlib:bsearch`, `cstdlib:abs` - `namespace std` memory allocation, process termination, conversion, and sorting imports.
- `cstdio:FILE`, `cstdio:fpos_t`, `cstdio:printf`, `cstdio:snprintf`, `cstdio:fopen`, `cstdio:fclose`, `cstdio:fread`, `cstdio:fwrite` - `namespace std` standard I/O stream imports.
- `cstring:memcpy`, `cstring:memmove`, `cstring:memset`, `cstring:strlen`, `cstring:strcmp`, `cstring:strncpy`, `cstddef:size_t`, `cstddef:ptrdiff_t`, `cstddef:nullptr_t`, `cstdint:int8_t`, `cstdint:uint64_t`, `ctime:clock_t`, `ctime:time_t`, `ctime:tm` - String, fixed-width integer, pointer-difference, and time declarations in `namespace std`.
- `cassert`, `cctype`, `cerrno`, `cinttypes`, `climits`, `clocale`, `csignal`, `cstdarg`, `cstdbool`, `cwchar`, `cwctype` - Standard C library header forwarders for C++ translation units.
- Subdirectories:
  - [./nuttx/README.md](./nuttx/README.md) - Internal `std::abs` overload helper (`std_abs.h`) shared by `<cstdlib>` and `<cmath>`.

## Invariants
- `cmath` undefines C99 classification macros (`signbit`, `fpclassify`, `isfinite`, `isinf`, `isnan`) and replaces them with overloaded `constexpr`/`inline` functions in `namespace std` so they do not conflict with C++ templates.

## Side Effects
- None at the header level; calling imported runtime functions (`cstdlib:malloc`, `cstdio:fopen`, `cstdlib:exit`) invokes the underlying NuttX C library implementations.

## Verification
- Run: `make test`
