# imxrt1180

## Overview
Host-side flash image packaging tools for NXP i.MX RT1180 targets (`tools/imxrt1180`). Provides both a standalone C utility (`mkahab`) that constructs an unsigned NXP AHAB (Advanced High-Assurance Boot) container with FIPS 180-4 SHA-256 image digests and a shell wrapper (`build_flash_image.sh`) that uses NXP's `spsdk` (`nxpimage ahab export`) to combine FlexSPI Configuration Block (FCB), optional EdgeLock Enclave (ELE) firmware, and the Cortex-M33 XIP binary into a bootable `flash.bin` image.

## Interface
- `mkahab.c:main` - CLI tool (`--m33 <nuttx.bin> --out <flash.bin>`) that extracts the FCB from offset `0x400`, builds a 160-byte unsigned AHAB container (`AHAB_TAG=0x87`, `AHAB_SIGBLK_TAG=0x90`) at flash offset `0x1000`, and places the Cortex-M33 XIP code at `M33_LOAD_ADDR` (`0x2800b000`).
- `sha256.h:sha256_ctx_s` - Context structure (`state`, `bitcount`, `buf`) for incremental SHA-256 hashing.
- `sha256.c:sha256_init`, `sha256.c:sha256_update`, `sha256.c:sha256_final`, `sha256.c:sha256_buffer` - FIPS 180-4 SHA-256 implementation used by `mkahab.c:main` to populate the 64-byte image hash field (`sha256_buffer`).
- `build_flash_image.sh:usage`, `build_flash_image.sh:SPSDK_VERSION` - Shell script (`--m33 <nuttx.bin> --out <flash.bin> [--ele-fw <container.img>]`) that provisions `spsdk==3.11.0` in `.cache/spsdk-venv` and runs `nxpimage ahab export` when EdgeLock Enclave firmware is included, or falls back to `mkahab`.
- `Config.mk:IMXRT_ELE_FW_ABS`, `Config.mk:POSTBUILD` - Build system post-build rules that optionally download `mxrt1180b0-ahab-container.img` when `CONFIG_IMXRT_ELE_FW_DOWNLOAD=y` and invoke `build_flash_image.sh`.

## Invariants
- Input `nuttx.bin` size must be strictly greater than `mkahab.c:CODE_FILE_OFFSET` (`0xac00`) and at most `mkahab.c:M33_MAX_SIZE` (`512 * 1024` bytes) so the Cortex-M33 XIP image does not overlap the Cortex-M7 flash partition at `0x28080000`.
- `mkahab.c:FCB_OFFSET` (`0x0400`), `mkahab.c:CONTAINER_OFFSET` (`0x1000`), and `mkahab.c:IMAGE_OFFSET` (`0xb000`) are fixed to match the i.MX RT1180 Boot ROM FlexSPI NOR layout.

## Side Effects
- `mkahab.c:main` and `build_flash_image.sh` allocate a flat flash buffer initialized to `0xff` and write the output image (`flash.bin`) to disk.
- `build_flash_image.sh` creates a Python virtual environment in `.cache/spsdk-venv` and installs `spsdk` via `pip` when invoked with `--ele-fw`.
- `Config.mk:POSTBUILD` downloads the NXP EdgeLock Enclave firmware container from GitHub via `curl` when `CONFIG_IMXRT_ELE_FW_DOWNLOAD=y` and the firmware file is missing.

## Verification
- Run: `make test`
