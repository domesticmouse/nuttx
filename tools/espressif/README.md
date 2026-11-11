# Espressif SoC Build, Bootloader, Flash & Diagnostics Tools

## Overview
Provides build scripts, Makefile/CMake post-build macros, eFuse key provisioning utilities, `esptool` version checks, and `nxdiag` vendor/chip metadata collectors for Espressif Xtensa and RISC-V SoCs (`esp32`, `esp32s2`, `esp32s3`, `esp32c2`, `esp32c3`, `esp32c6`, `esp32h2`, `esp32p4`).

## Interface
- `build_mcuboot.sh:build_mcuboot`, `build_mcuboot.sh:usage` - Builds the Espressif MCUboot bootloader (`mcuboot-<chip>.bin`) using CMake/Ninja against `esp-hal-3rdparty`.
- `build_mcuboot_esp32c3_legacy.sh:build_mcuboot`, `build_mcuboot_esp32c3_legacy.sh:usage` - Legacy MCUboot build script for ESP32-C3 targets.
- `burn_flash_enc_key.py:main` - Burns the `XTS_AES_128_KEY` flash encryption key into `BLOCK_KEY0` hardware eFuses via `espefuse.py` when `NUTTX_ESPEFUSE`, `ESPTOOL_PORT`, `NUTTX_KEY`, and `NOCHECK` are set in the environment.
- `check_esptool.py:check_version`, `check_esptool.py:parse_version` - Verifies that the installed `esptool.py` meets the minimum required version (`-v <version>`).
- `chip_info.py:get_vendor_info`, `chip_info.py:get_espressif_bootloader_version`, `chip_info.py:get_espressif_toolchain_version`, `chip_info.py:get_espressif_hal_version`, `chip_info.py:get_espressif_chip_id`, `chip_info.py:get_espressif_flash_id`, `chip_info.py:get_espressif_security_info`, `chip_info.py:get_espressif_flash_status`, `chip_info.py:get_espressif_mac_address` - Queries host toolchains, bootloader binaries, HAL git tags, and connected hardware via `esptool.py` to generate C arrays for `sysinfo.h` (`nxdiag`).
- `Config.mk:POSTBUILD`, `Config.mk:MKIMAGE`, `Config.mk:MERGEBIN`, `Config.mk:MAKEUF2`, `Config.mk:FLASH_ENC`, `Config.mk:BURN_EFUSES`, `Config.mk:FLASH` - Makefile macros for converting ELF to MCUboot/ESP images, encrypting SPI flash partitions, merging binaries/UF2 images, burning eFuses, and flashing targets.

## Invariants
- `burn_flash_enc_key.py:main` refuses to run unless `NUTTX_ESPEFUSE`, `ESPTOOL_PORT`, `NUTTX_KEY`, and the explicit confirmation bypass `NOCHECK` are set in `os.environ`, and skips burning if `BLOCK1` in `espefuse.py summary` already contains `?? ??` (key read-protected/burned).
- `check_esptool.py:check_version` returns `False` (exit code `0`) when `esptool.py` is installed and `>= min_esptool_version`, and `True` (exit code `1`) when missing or outdated.

## Side Effects
- Irreversibly programs hardware eFuses (`BLOCK_KEY0`) via `espefuse.py` in `burn_flash_enc_key.py:main` and `Config.mk:BURN_EFUSES`.
- Queries and resets attached Espressif hardware over serial via `esptool.py` (`chip_info.py:run_espressif_tool`) and flashes firmware images (`Config.mk:FLASH`).
- Compiles MCUboot binaries in `${exec_path}/mcuboot` and writes `mcuboot-<target>.bin` to `${exec_path}/out` (`build_mcuboot.sh:build_mcuboot`).

## Verification
- Run: `make test`
