# eFuse Subsystem Headers (`include/nuttx/efuse`)

## Overview
Defines the NuttX eFuse (One-Time Programmable memory) upper-half character driver interface, bit-field descriptors, `ioctl` commands, lower-half operation tables, and Microchip SAMA5 Secure Fuse Controller (SFC) fuse bitmaps.

## Interface
- `efuse.h:EFUSEIOC_READ_FIELD`, `efuse.h:EFUSEIOC_WRITE_FIELD`, `efuse.h:EFUSEIOC_MASK` - eFuse `ioctl` commands for reading, burning, and masking fuse fields.
- `efuse.h:efuse_desc_s`, `efuse.h:efuse_desc_t`, `efuse.h:efuse_param_s` - Bit-offset and bit-count field descriptor and `ioctl` parameter wrapper.
- `efuse.h:efuse_ops_s`, `efuse.h:efuse_lowerhalf_s`, `efuse.h:efuse_register`, `efuse.h:efuse_unregister` - Lower-half eFuse operations (`read_field`, `write_field`, `ioctl`) and VFS character driver registration/unregistration.
- `sama5_sfc_fuses.h:SAM_SFC_EFUSE_MAX_LEN`, `sama5_sfc_fuses.h:SAMA5_SFC_DATA0` .. `sama5_sfc_fuses.h:SAMA5_SFC_JTAG_DIS` - SAMA5D2/SAMA5D4 SFC eFuse register indices and static `efuse_desc_t` bitfield descriptors.

## Invariants
- `efuse.h:efuse_param_s.field` must be a NULL-terminated array of `efuse_desc_t *` descriptors whose cumulative `bit_count` matches the bit size passed to `read_field` or `write_field`.
- `sama5_sfc_fuses.h:SAM_SFC_EFUSE_MAX_LEN` is `544` bits on `ATSAMA5D2` and `512` bits on `ATSAMA5D4`.

## Side Effects
- `efuse.h:efuse_register` and `efuse.h:efuse_unregister` create and remove an eFuse character device node in the VFS.
- `efuse.h:efuse_ops_s.write_field` (and `EFUSEIOC_WRITE_FIELD`) permanently blows hardware OTP fuse bits in non-volatile silicon storage.

## Verification
- Run: `make test`
