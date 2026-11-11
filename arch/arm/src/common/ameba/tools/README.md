# tools (`nuttx/arch/arm/src/common/ameba/tools`)

## Overview
Hardware abstraction and architecture package for `tools` under `nuttx/arch/arm/src/common/ameba/tools`, providing 0 header file(s) and 11 source file(s) (including `ameba_asdk_version.sh`, `ameba_build_np.sh`, `ameba_fetch_sdk.sh`, `ameba_fetch_toolchain.sh`).

## Interface
- `[ameba_asdk_version.sh:main]`
- `[ameba_build_np.sh:collect]`
- `[ameba_build_np.sh:stage_cfg]`
- `[ameba_build_np.sh:main]`
- `[ameba_fetch_sdk.sh:main]`
- `[ameba_fetch_toolchain.sh:main]`
- `[ameba_flash.sh:main]`
- `[ameba_gen_autoconf.sh:main]`
- `[ameba_gen_ldscript.sh:main]`
- `[ameba_package.sh:main]`
- `[ameba_sdk_config.sh:main]`
- `[ameba_setup_env.sh:py_has_deps]`
- `[ameba_setup_env.sh:resolve_bindir]`
- `[ameba_setup_env.sh:publish_bindir]`
- `[ameba_setup_env.sh:main]`
- `[ameba_smart_flash.sh:main]`

## Invariants
- None

## Side Effects
- `[ameba_asdk_version.sh:sh]` Executes shell commands and filesystem operations
- `[ameba_build_np.sh:sh]` Executes shell commands and filesystem operations
- `[ameba_fetch_sdk.sh:sh]` Executes shell commands and filesystem operations
- `[ameba_fetch_toolchain.sh:sh]` Executes shell commands and filesystem operations
- `[ameba_flash.sh:sh]` Executes shell commands and filesystem operations
- `[ameba_gen_autoconf.sh:sh]` Executes shell commands and filesystem operations
- `[ameba_gen_ldscript.sh:sh]` Executes shell commands and filesystem operations
- `[ameba_package.sh:sh]` Executes shell commands and filesystem operations
- `[ameba_sdk_config.sh:sh]` Executes shell commands and filesystem operations
- `[ameba_setup_env.sh:sh]` Executes shell commands and filesystem operations
- `[ameba_smart_flash.sh:sh]` Executes shell commands and filesystem operations

## Verification
- Run: `make test`
