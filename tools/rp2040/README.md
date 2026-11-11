# rp2040

## Overview
Host-side build rules and SmartFS flash filesystem generator (`tools/rp2040`) for Raspberry Pi RP2040 targets. Provides `make_flash_fs` to convert a prototype host directory tree into a Cortex-M0+ assembly file containing a pre-formatted SmartFS flash image (`rp2040_smart_flash_start` to `rp2040_smart_flash_end`), and `Config.mk` macros to verify `PICO_SDK_PATH` stage-2 bootloaders and generate UF2 images via `picotool`.

## Interface
- `make_flash_fs.c:main`, `make_flash_fs.c:scan_dir`, `make_flash_fs.c:copy_file` - CLI tool (`make_flash_fs [-h] [-n name-len] source-path`) that walks `source-path` and emits `.flash.init` section assembly macros (`sector`, `dir_entry`, `file_entry`) to stdout.
- `Config.mk:PREBUILD`, `Config.mk:POSTBUILD`, `Config.mk:GEN_PICO_UF2` - Make macros that validate `boot2_$(BOOT2_FLASH_CHIP).S` in `PICO_SDK_PATH` when `CONFIG_RP2040_FLASH_BOOT=y` and convert `nuttx` ELF to `nuttx.uf2` when `CONFIG_RP2040_UF2_BINARY=y`.

## Invariants
- `make_flash_fs.c:max_name_len` (default `MAX_NAME_LEN = 16`, configurable via `-n`) must match `CONFIG_SMARTFS_MAXNAMLEN` in the target NuttX configuration; files with names exceeding `max_name_len` are skipped.
- When `CONFIG_RP2040_FLASH_BOOT=y`, `PICO_SDK_PATH` must point to a valid `pico-sdk` checkout containing `src/rp2040/boot_stage2/boot2_$(BOOT2_FLASH_CHIP).S`.

## Side Effects
- `make_flash_fs.c:main` reads the host directory hierarchy under `source-path` and writes SmartFS assembly definitions to stdout.
- `Config.mk:POSTBUILD` may configure and build `picotool` inside `$(PICO_SDK_PATH)` via `cmake` and `make picotoolBuild` if `picotool` is not on `PATH`, and writes `nuttx.uf2` and appends to `nuttx.manifest`.

## Verification
- Run: `make test`
