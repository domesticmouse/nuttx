<uClibc++ System Configuration (`libs/libxx/uClibc++`)>
## Overview
Provides the NuttX integration header (`system_configuration.h`) for the `uClibc++` embedded C++ standard library. It bridges NuttX Kconfig options (`<nuttx/config.h>`) to `uClibc++` build and feature macros (`__UCLIBCXX_*`).

## Interface
- `system_configuration.h:__UCLIBCXX_MAJOR__`, `system_configuration.h:__UCLIBCXX_MINOR__`, `system_configuration.h:__UCLIBCXX_SUBLEVEL__` - Defines the targeted `uClibc++` version (`0.2.6-git`).
- `system_configuration.h:__UCLIBCXX_HAS_FLOATS__` and `system_configuration.h:__UCLIBCXX_HAS_LONG_DOUBLE__` - Conditionally enables floating-point support based on `CONFIG_HAVE_FLOAT` and `CONFIG_HAVE_LONG_DOUBLE`.
- `system_configuration.h:__UCLIBCXX_HAS_WCHAR__`, `system_configuration.h:__UCLIBCXX_SUPPORT_WCIN__`, `system_configuration.h:__UCLIBCXX_SUPPORT_WCOUT__`, `system_configuration.h:__UCLIBCXX_SUPPORT_WCERR__`, `system_configuration.h:__UCLIBCXX_SUPPORT_WCLOG__` - Conditionally enables wide-character and wide-stream support when `CONFIG_CXX_WCHAR` is set.
- `system_configuration.h:__UCLIBCXX_IOSTREAM_BUFSIZE__` and `system_configuration.h:__UCLIBCXX_STL_BUFFER_SIZE__` - Maps stream and STL buffer sizes to `CONFIG_UCLIBCXX_BUFSIZE`.
- `system_configuration.h:__UCLIBCXX_EXCEPTION_SUPPORT__` and `system_configuration.h:__DODEBUG__` - Enables C++ exception support (`CONFIG_CXX_EXCEPTION`) and debug assertions (`CONFIG_DEBUG_ASSERTIONS`).

## Invariants
- `system_configuration.h:__UCLIBCXX_HAS_TLS__`, `system_configuration.h:__UCLIBCXX_HAS_LFS__`, `system_configuration.h:__IMPORT_LIBSUP__`, and `system_configuration.h:__IMPORT_LIBGCC_EH__` are explicitly undefined (`#undef`) so `uClibc++` builds as a self-contained static library (`__BUILD_STATIC_LIB__`) over NuttX runtime primitives.

## Side Effects
- None (header-only preprocessor configuration).

## Verification
- Run: `make test`
</uClibc++ System Configuration (`libs/libxx/uClibc++`)>
