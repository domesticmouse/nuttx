# Flattened Device Tree Library Glue (`libs/libc/fdt`)

## Overview
Provides the build configuration and version header (`version_gen.h`) required to compile the external Flattened Device Tree library (`libfdt`) into the NuttX C library when `CONFIG_LIBC_FDT` is enabled.

## Interface
- `[version_gen.h:DTC_VERSION]` - Macro expanding to `CONFIG_LIBC_FDT_DTC_VERSION` to identify the `libfdt` / Device Tree Compiler version string.

## Invariants
- `CONFIG_LIBC_FDT_DTC_VERSION` must be defined by Kconfig when `version_gen.h` is included (`[version_gen.h:DTC_VERSION]`).

## Side Effects
- None

## Verification
- Run: `make test`
