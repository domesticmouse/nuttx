# Timezone ROMFS Image Wrapper (`libs/libc/zoneinfo`)

## Overview
Builds and embeds an optional ROMFS filesystem image (`romfs_zoneinfo.h`) containing compiled IANA Olson timezone (`tzdata`) definitions into `libc` when `CONFIG_LIBC_ZONEINFO_ROMFS` is enabled.

## Interface
- `tzromfs.c:romfs_zoneinfo_img`, `tzromfs.c:romfs_zoneinfo_img_len` - Includes `<nuttx/zoneinfo.h>` and the build-generated `romfs_zoneinfo.h` byte array (`xxd -i romfs_zoneinfo.img`) to export the read-only timezone ROMFS image to the kernel/application mount logic.

## Invariants
- `tzromfs.c` is only compiled when `CONFIG_LIBC_ZONEINFO_ROMFS` is enabled and `romfs_zoneinfo.h` has been generated from the compiled `tzbin/usr/share/zoneinfo` directory via `genromfs` and `xxd`.

## Side Effects
- None at runtime (defines read-only static image data in `.rodata`).

## Verification
- Run: `make test`
