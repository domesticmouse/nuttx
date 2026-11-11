# CI Tools

## Overview
These are tools and data used for the CI system. Some of what is here may also be useful for local testing. This component orchestrates continuous integration builds, out-of-tree (OOT) export builds, repository setup, `ccache` configuration, and platform-specific toolchain installation across Unix and Windows hosts.

## Interface
- `cibuild.sh:install_tools`, `cibuild.sh:enable_ccache`, `cibuild.sh:setup_repos`, `cibuild.sh:run_builds`, `cibuild.sh:usage` - Primary Bash CI entry point (`cibuild.sh [-i] [-s] [-c] [-*] <testlist>`) that dispatches platform provisioning scripts and runs `tools/testbuild.sh` across `<testlist>` files.
- `cibuild.ps1:install_tools`, `cibuild.ps1:enable_ccache`, `cibuild.ps1:setup_repos`, `cibuild.ps1:run_builds`, `cibuild.ps1:usage` - Native Windows PowerShell CI entry point (`cibuild.ps1 [-h] [-i] [-s] [-c] [-*] <testlist>`) that invokes `platforms/windows.ps1` and `tools/testbuild.ps1`.
- `cibuild-oot.sh:EXPORT_CONFIG`, `cibuild-oot.sh:OOT_SRC`, `cibuild-oot.sh:BUILD_DIR` - Out-of-tree CI validation script that configures a NuttX export target (`./tools/configure.sh -E -l`), builds the export tarball (`make export`), unpacks it into `OOT_SRC`, and builds the external CMake project using the exported `toolchain.cmake`.
- `./platforms/README.md` - Platform-specific toolchain and dependency installation scripts for Darwin, Linux, Ubuntu, MSYS2, and Windows.

## Invariants
- `cibuild.sh:run_builds` and `cibuild.ps1:run_builds` require at least one `<testlist>` argument or terminate via `usage`.
- `cibuild-oot.sh` requires `make export` to produce a `nuttx-export-*.tar.gz` containing `scripts/toolchain.cmake` and verifies that both `oot` and `oot.bin` artifacts are produced in `BUILD_DIR`.

## Side Effects
- Clones or pulls `apache/nuttx` and `apache/nuttx-apps` git repositories when `-s` is passed (`cibuild.sh:setup_repos`, `cibuild.ps1:setup_repos`).
- Installs toolchains into `${CIWORKSPACE}/tools` and sources `${CIWORKSPACE}/tools/env.sh` when `-i` is passed (`cibuild.sh:install_tools`, `cibuild.ps1:install_tools`).
- Executes full multi-core test builds via `tools/testbuild.sh` / `tools/testbuild.ps1` and builds/cleans out-of-tree directories in `cibuild-oot.sh`.

## Verification
- Run: `make test`
