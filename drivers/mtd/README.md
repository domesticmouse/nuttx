# Memory Technology Device (MTD) Drivers (`drivers/mtd`)

## Overview
Implements the Memory Technology Device (MTD) subsystem in NuttX, including NOR/NAND flash and EEPROM/FRAM chip drivers (SPI, QSPI, I2C, parallel CFI, progmem, RAM, file-backed, and RPMSG remote flash), NAND ECC/ONFI/bad-block management, flash translation layers (`ftl`, `dhara`, `smart`, `nvblk`), partitioning, and NVS configuration storage.

## Interface
- `[mtd_partition.c:mtd_partition]`, `[mtd_partition.c:mtd_setpartitionname]` - Creates logical sub-region MTD partitions (`[mtd_partition.c:struct mtd_partition_s]`) and exposes `/proc/partitions`.
- `[ftl.c:ftl_initialize]`, `[ftl.c:ftl_initialize_by_path]`, `[dhara.c:dhara_initialize]`, `[dhara.c:dhara_initialize_by_path]`, `[smart.c:smart_initialize]`, `[nvblk.c:nvblk_initialize]`, `[sector512.c:s512_initialize]`, `[mtd_rwbuffer.c:mtd_rwb_initialize]` - Block-device translation, wear-leveling, sector-size conversion, and caching wrappers over MTD devices.
- `[mtd_config.c:mtdconfig_register]`, `[mtd_config.c:mtdconfig_register_by_path]`, `[mtd_config_nvs.c:mtdconfig_register]`, `[mtd_config_nvs.c:mtdconfig_unregister]` - Non-volatile configuration storage (`/dev/config`) backed by raw MTD or NVS flash (`[mtd_config_nvs.c:struct nvs_fs]`).
- `[mtd_nand.c:nand_initialize]`, `[mtd_nand.c:nand_raw_initialize]`, `[mtd_nandwrapper.c:nand_wrapper_initialize]`, `[mtd_nandram.c:nand_ram_initialize]`, `[mtd_onfi.c:onfi_read]`, `[mtd_nandecc.c:nandecc_readpage]`, `[mtd_nandecc.c:nandecc_writepage]`, `[hamming.c:hamming_compute256x]`, `[hamming.c:hamming_verify256x]` - NAND flash core, ONFI detection, spare-area schemes, and Hamming ECC.
- `[cfi.h:cfi_check]`, `[cfi.h:cfi_read]`, `[cfi.h:cfi_write]`, `[cfi.h:cfi_erase]`, `[mtd_cfi.c:register_cfi_driver]` - Parallel Common Flash Interface (CFI) NOR flash driver (`[cfi.h:struct cfi_dev_s]`).
- `[filemtd.c:filemtd_initialize]`, `[filemtd.c:mtd_loop_register]`, `[rammtd.c:rammtd_initialize]`, `[nullmtd.c:nullmtd_initialize]`, `[mtd_progmem.c:progmem_initialize]`, `[rpmsgmtd.c:rpmsgmtd_register]`, `[rpmsgmtd_server.c:rpmsgmtd_server_init]` - Virtual, on-chip progmem, and RPMSG remote MTD drivers.
- `[w25.c:w25_initialize]`, `[w25n.c:w25n_initialize]`, `[w25qxxxjv.c:w25qxxxjv_initialize]`, `[gd25.c:gd25_initialize]`, `[gd55.c:gd55_initialize]`, `[gd5f.c:gd5f_initialize]`, `[mx25lx.c:mx25l_initialize_spi]`, `[mx25rxx.c:mx25rxx_initialize]`, `[mx25uw25645g.c:mx25uw25645g_initialize]`, `[mx35.c:mx35_initialize]`, `[mx66uw1g45g.c:mx66uw1g45g_initialize]`, `[at24xx.c:at24c_initialize]`, `[at25.c:at25_initialize]`, `[at25ee.c:at25ee_initialize]`, `[at45db.c:at45db_initialize]`, `[is25xp.c:is25xp_initialize]`, `[m25px.c:m25p_initialize]`, `[n25qxxx.c:n25qxxx_initialize]`, `[ramtron.c:ramtron_initialize]`, `[s25fl1.c:s25fl1_initialize]`, `[sst25.c:sst25_initialize]`, `[sst25xx.c:sst25xx_initialize]`, `[sst26.c:sst26_initialize_spi]`, `[sst39vf.c:sst39vf_initialize]` - Hardware flash/EEPROM/FRAM chip initializers.

## Invariants
- Partition boundaries (`[mtd_partition.c:firstblock]` + `nblocks`) must lie within the parent MTD geometry and align to erase block boundaries (`[mtd_partition.c:blkpererase]`).
- Concurrent flash translation, NVS, NAND, and RPMSG MTD operations are serialized using per-device mutexes (`[dhara.c:nxmutex_lock]`, `[mtd_config_nvs.c:nxmutex_lock]`, `[mtd_nand.c:nxmutex_lock]`, `[nvblk.c:nxmutex_lock]`, `[rpmsgmtd.c:nxmutex_lock]`).

## Side Effects
- Performs erase, block read/write, and byte write cycles on physical SPI, QSPI, I2C, parallel memory-mapped, and on-chip flash media (`SPI_SEND`, `I2C_TRANSFER`, `up_progmem_*`).
- Registers block and character drivers (`[ftl.c:register_blockdriver]`, `[smart.c:register_blockdriver]`, `[nvblk.c:register_blockdriver]`, `[filemtd.c:register_driver]`) and exchanges RPMSG IPC packets (`[rpmsgmtd.c:rpmsg_create_ept]`).

## Verification
- Run: `make test`
