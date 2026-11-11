# CI Platform Toolchains & Environment Setup

## Overview
Platform-specific provisioning scripts invoked by the NuttX CI runner (`cibuild.sh` / `cibuild.ps1`) to download, build, and configure cross-compilation toolchains, host utilities, SDKs, Python packages, and `ccache` symlinks across macOS (Intel and Apple Silicon), Linux, Ubuntu, MSYS2, and Windows native environments.

## Interface
- `darwin.sh:install_build_tools`, `darwin.sh:setup_links`, `darwin.sh:add_path` - Provisions macOS x86_64 CI build tools (`arm_clang_toolchain`, `arm_gcc_toolchain`, `arm64_gcc_toolchain`, `avr_gcc_toolchain`, `binutils`, `bloaty`, `elf_toolchain`, `gen_romfs`, `gperf`, `kconfig_frontends`, `mips_gcc_toolchain`, `python_tools`, `riscv_gcc_toolchain`, `rust`, `dlang`, `zig`, `xtensa_esp_gcc_toolchain`, `u_boot_tools`, `util_linux`, `wasi_sdk`, `c_cache`).
- `darwin_arm64.sh:install_build_tools`, `darwin_arm64.sh:setup_links`, `darwin_arm64.sh:add_path` - Provisions macOS ARM64 (Apple Silicon) CI build tools and toolchains.
- `linux.sh:install_build_tools`, `linux.sh:setup_links`, `linux.sh:add_path` - Provisions generic Linux x86_64 CI toolchains including `rx_gcc_toolchain`, `sparc_gcc_toolchain`, and `raspberrypi_pico_sdk`.
- `ubuntu.sh:install_build_tools`, `ubuntu.sh:setup_links`, `ubuntu.sh:add_path` - Provisions Ubuntu CI build tools via `apt-get` and prebuilt archives (`clang_tidy`, `avr_gcc_toolchain`, `u_boot_tools`, `raspberrypi_pico_sdk`, etc.).
- `msys2.sh:install_build_tools`, `msys2.sh:setup_links`, `msys2.sh:add_path` - Provisions MSYS2 Windows CI build tools and toolchains (`esp_tool`, `gen_romfs`, `kconfig_frontends`, `rust`, etc.).
- `windows.ps1:install_build_tools`, `windows.ps1:add_path`, `windows.ps1:add_envpath` - PowerShell provisioning script for native Windows CI toolchains (`cmake_tool`, `ninja_tool`, `pico_sdk`, `pico_tool`, `esp_tool`, `kconfig_frontends`).

## Invariants
- `NUTTXTOOLS` environment variable must be defined prior to invoking `install_build_tools` in `darwin.sh:install_build_tools`, `darwin_arm64.sh:install_build_tools`, `linux.sh:install_build_tools`, `ubuntu.sh:install_build_tools`, `msys2.sh:install_build_tools`, and `windows.ps1:install_build_tools`.
- Each script writes environment exports (`PATH`, `WASI_SDK_PATH`, `PICO_SDK_PATH`, `PYTHONUSERBASE`, `CARGO_HOME`, `RUSTUP_HOME`) to `${NUTTXTOOLS}/env.sh` (or `$NUTTXTOOLS\env.ps1` on Windows).

## Side Effects
- Downloads toolchain archives and clones repositories from GitHub, ARM, Espressif, Gaisler, Renesas, and GNU mirrors into `${NUTTXTOOLS}` across `darwin.sh:install_build_tools`, `darwin_arm64.sh:install_build_tools`, `linux.sh:install_build_tools`, `ubuntu.sh:install_build_tools`, `msys2.sh:install_build_tools`, and `windows.ps1:install_build_tools`.
- Installs system packages via `brew` (`darwin.sh:install_build_tools`, `darwin_arm64.sh:install_build_tools`), `sudo apt-get` (`ubuntu.sh:install_build_tools`), `pacman` (`msys2.sh:c_cache`), and `pip3` (`python_tools`).
- Creates compiler wrapper symlinks in `${NUTTXTOOLS}/ccache/bin` via `setup_links` and writes `${NUTTXTOOLS}/env.sh` / `${NUTTXTOOLS}/env.ps1`.

## Verification
- Run: `make test`
