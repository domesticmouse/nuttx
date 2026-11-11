# Memory Technology Device (MTD) Interfaces (`include/nuttx/mtd`)

## Overview
Defines the Memory Technology Device (MTD) subsystem interfaces for NOR, NAND, EEPROM, QSPI, and RAM/file-backed flash storage in NuttX. Includes the core MTD driver vtable, partitioning, FTL, and SMART filesystem initializers (`mtd.h`), persistent configuration data storage (`configdata.h`), software Hamming ECC (`hamming.h`), NAND flash upper/lower-half layers, ONFI detection, spare area schemes, and model tables (`nand.h`, `nand_raw.h`, `nand_ecc.h`, `nand_model.h`, `nand_scheme.h`, `nand_wrapper.h`, `nand_ram.h`, `onfi.h`), and SMART flash layer debug structures (`smart.h`).

## Interface
- `mtd.h:struct mtd_dev_s`, `mtd.h:struct mtd_geometry_s`, `mtd.h:struct mtd_protect_s`, `mtd.h:struct mtd_erase_s`, `mtd.h:struct mtd_bad_block_s`, `mtd.h:MTD_ERASE`, `mtd.h:MTD_BREAD`, `mtd.h:MTD_BWRITE`, `mtd.h:MTD_READ`, `mtd.h:MTD_WRITE`, `mtd.h:MTD_IOCTL`, `mtd.h:MTD_ISBAD`, `mtd.h:MTD_MARKBAD`, `mtd.h:mtd_partition`, `mtd.h:mtd_rwb_initialize`, `mtd.h:ftl_initialize`, `mtd.h:smart_initialize`, `mtd.h:filemtd_initialize`, `mtd.h:nullmtd_initialize`, `mtd.h:rpmsgmtd_register`, `mtd.h:dhara_initialize`, `mtd.h:nvblk_initialize`
- `configdata.h:struct config_data_s`, `configdata.h:mtdconfig_register`, `configdata.h:mtdconfig_unregister`, `configdata.h:mtdconfig_register_by_path`, `configdata.h:mtdconfig_unregister_by_path`, `configdata.h:CFGDIOC_GETCONFIG`, `configdata.h:CFGDIOC_SETCONFIG`, `configdata.h:CFGDIOC_DELCONFIG`
- `hamming.h:hamming_compute256x`, `hamming.h:hamming_verify256x`, `hamming.h:HAMMING_SUCCESS`, `hamming.h:HAMMING_ERROR_SINGLEBIT`, `hamming.h:HAMMING_ERROR_MULTIPLEBITS`
- `nand.h:struct nand_dev_s`, `nand.h:nand_initialize`, `nand.h:nand_raw_initialize`
- `nand_config.h:CONFIG_MTD_NAND_MAXNUMBLOCKS`, `nand_config.h:CONFIG_MTD_NAND_MAXPAGEDATASIZE`, `nand_config.h:CONFIG_MTD_NAND_MAXPAGESPARESIZE`
- `nand_ecc.h:nandecc_readpage`, `nand_ecc.h:nandecc_writepage`
- `nand_model.h:struct nand_model_s`, `nand_model.h:g_nandmodels`, `nand_model.h:nandmodel_find`, `nand_model.h:nandmodel_translate`, `nand_model.h:nandmodel_pagesperblock`
- `nand_ram.h:nand_ram_initialize`, `nand_ram.h:nand_ram_eraseblock`, `nand_ram.h:nand_ram_rawread`, `nand_ram.h:nand_ram_rawwrite`
- `nand_raw.h:struct nand_raw_s`, `nand_raw.h:WRITE_COMMAND8`, `nand_raw.h:WRITE_ADDRESS8`, `nand_raw.h:WRITE_DATA8`, `nand_raw.h:READ_DATA8`, `nand_raw.h:NAND_ERASEBLOCK`, `nand_raw.h:NAND_RAWREAD`, `nand_raw.h:NAND_RAWWRITE`
- `nand_scheme.h:struct nand_scheme_s`, `nand_scheme.h:g_nand_sparescheme256`, `nand_scheme.h:g_nand_sparescheme512`, `nand_scheme.h:g_nand_sparescheme2048`, `nand_scheme.h:g_nand_sparescheme4096`, `nand_scheme.h:nandscheme_readbadblockmarker`, `nand_scheme.h:nandscheme_writebadblockmarker`, `nand_scheme.h:nandscheme_readecc`, `nand_scheme.h:nandscheme_writeecc`
- `nand_wrapper.h:struct nand_wrapper_dev_s`, `nand_wrapper.h:nand_wrapper_initialize`, `nand_wrapper.h:nand_wrapper_erase`, `nand_wrapper.h:nand_wrapper_bread`, `nand_wrapper.h:nand_wrapper_bwrite`
- `onfi.h:struct onfi_pgparam_s`, `onfi.h:onfi_compatible`, `onfi.h:onfi_read`, `onfi.h:onfi_embeddedecc`, `onfi.h:onfi_ebidetect`
- `smart.h:struct mtd_smart_procfs_data_s`, `smart.h:struct mtd_smart_debug_data_s`, `smart.h:struct smart_alloc_s`

## Invariants
- `mtd.h:MTD_ERASE`, `mtd.h:MTD_BREAD`, `mtd.h:MTD_BWRITE`, `mtd.h:MTD_READ`, `mtd.h:MTD_WRITE`, and `mtd.h:MTD_IOCTL` return `-ENOSYS` if the corresponding function pointer in `mtd.h:struct mtd_dev_s` is `NULL`.
- `nand.h:struct nand_dev_s` serializes concurrent flash access using its internal `lock` mutex.

## Side Effects
- Invoking `mtd.h:struct mtd_dev_s` and `nand_raw.h:struct nand_raw_s` operations erases flash blocks, programs pages, mutates spare/OOB bad-block markers, and performs memory-mapped (`nand_raw.h:WRITE_COMMAND8`), SPI, or QSPI bus I/O.
- `ftl_initialize`, `smart_initialize`, `dhara_initialize`, `nvblk_initialize`, and `mtdconfig_register` register block or character devices in the VFS namespace.

## Verification
- Run: `make test`
