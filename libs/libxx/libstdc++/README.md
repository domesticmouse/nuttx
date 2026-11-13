# GNU `libstdc++` Platform Configuration (`libs/libxx/libstdc++`)

## Overview
Provides the NuttX platform configuration header (`c++config.h`) and build rules (`libsupc++.defs`, `CMakeLists.txt`) for integrating the GNU ISO C++ Library (`libstdc++` release 13 / `libsupc++`) with NuttX (`CONFIG_LIBSTDCXX` / `CONFIG_LIBSUPCXX`).

## Interface
- `[c++config.h:_GLIBCXX_RELEASE]` GNU `libstdc++` platform and ABI configuration macros (`_GLIBCXX_RELEASE`, `__GLIBCXX__`, `_GLIBCXX_HOSTED`, `_GLIBCXX_USE_C99_STDINT_TR1`, `_GLIBCXX_HAS_GTHREADS`, `_GLIBCXX_ATOMIC_BUILTINS`)
- `[libsupc++.defs:SUPSRCS]` Make build rules (`copy_headers`, `SUPSRCS`) downloading and compiling GNU `gcc/libstdc++-v3/libsupc++` sources (`CONFIG_LIBSTDCXX_VERSION`)
- `[CMakeLists.txt:CONFIG_LIBSUPCXX]` CMake build rules (`FetchContent_Declare(libstdcxx ...)`) downloading `libstdc++-v3.tar.gz` and copying `c++config.h` and `gthr`/`unwind-pe.h` headers

## Invariants
- `[libsupc++.defs:CPU_CONFIG]` Selects `arm` `cxxabi_tweaks.h` when `CONFIG_ARCH_ARM=y` and `generic` otherwise; `[libsupc++.defs:RTTI_SUPSRCS]` excludes `eh_arm.cc` and `eh_call.cc` unless `CONFIG_CXX_RTTI=y`.

## Side Effects
- `[libsupc++.defs:libstdc++-v3.tar.gz]` and `[CMakeLists.txt:libstdcxx]` Download and unpack the upstream GCC `libstdc++-v3.tar.gz` archive during build setup if `libstdc++/libstdc++/.git` is not already present, and copy `c++config.h`, `gthr.h`, `gthr-posix.h`, and `unwind-pe.h` into the build/include directories.

## Verification
- Run: `make test`
