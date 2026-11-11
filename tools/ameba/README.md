# Realtek Ameba Build & SDK Configuration Tools

## Overview
Provides shell scripts and Makefile fragments for integrating the Realtek Ameba (`rtl8721dx` / `rtl8720f`) vendor SDK (`ameba-rtos`) with the NuttX build system, including interactive SDK Kconfig overlay editing, toolchain environment provisioning, and image flashing.

## Interface
- `ameba_menuconfig.sh:getcfg` - Interactive wrapper around `ameba.py menuconfig` that loads and saves board-specific SDK Kconfig overlays (`boards/arm/<chip>/<board>/ameba_sdk.conf`) while enforcing mandatory options from `ameba_sdk_force.conf`.
- `env.sh:_ameba_board_list`, `env.sh:AMEBA_SDK`, `env.sh:AMEBA_TOOLCHAIN_DIR`, `env.sh:GCCVER` - Sourceable environment setup script (`. tools/ameba/env.sh [<board>[:config]]`) that fetches/locates the `ameba-rtos` SDK, the SoC-matched `asdk` toolchain, prebuilts, and Python virtualenv, and prepends them to `PATH`.
- `Config.mk:FLASH`, `Config.mk:ameba_menuconfig`, `Config.mk:AMEBA_BAUD` - Makefile fragment defining the `FLASH` post-build flashing macro (invoking `ameba_flash.sh`) and the `.PHONY` target `ameba_menuconfig`.

## Invariants
- `env.sh:AMEBA_SDK` must be sourced (`. tools/ameba/env.sh`), not executed directly as a subprocess (`case "$0" in *env.sh) exit 1`), so exported environment variables (`AMEBA_SDK`, `AMEBA_TOOLCHAIN_DIR`, `GCCVER`, `PATH`) persist in the caller shell.
- `ameba_menuconfig.sh:getcfg` requires an existing top-level `.config` configured for an Ameba chip (`CONFIG_ARCH_CHIP` equal to `rtl8721dx` or `rtl8720f`) and re-applies `ameba_sdk_force.conf` after the interactive TUI exits so forced SDK options cannot be overridden.
- `Config.mk:AMEBA_PREV_GOAL` preserves and restores `.DEFAULT_GOAL` around the `ameba_menuconfig` target definition so `all` remains the default Make goal.

## Side Effects
- `env.sh:AMEBA_SDK` invokes `ameba_fetch_sdk.sh`, `ameba_fetch_toolchain.sh`, and `ameba_setup_env.sh`, downloading the Realtek SDK, `asdk` cross-compiler, and prebuilts to disk and mutating `PATH`, `AMEBA_SDK`, `AMEBA_TOOLCHAIN_DIR`, and `GCCVER`.
- `ameba_menuconfig.sh:getcfg` unsets NuttX Kconfig/Make environment variables, runs `ameba.py menuconfig`, and writes the diff-vs-default overlay to `boards/arm/<chip>/<board>/ameba_sdk.conf`.
- `Config.mk:FLASH` flashes `boot.bin` and `nuttx.bin` over the serial port (`AMEBA_PORT` at `AMEBA_BAUD`).

## Verification
- Run: `make test`
