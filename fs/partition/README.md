# Disk and Flash Partition Table Parsers (`fs/partition`)

## Overview
Provides partition table discovery and parsing for block devices and MTD flash devices, supporting GUID Partition Table (GPT), Master Boot Record (MBR), PTABLE, and TXTABLE partition layouts.

## Interface
- `fs_partition.c:parse_block_partition` - Opens a block device (`open_blockdriver`), parses all configured partition table formats, and invokes `partition_handler_t` for each discovered partition.
- `fs_partition.c:parse_mtd_partition` - Wraps an `struct mtd_dev_s` instance, parses all configured partition table formats, and invokes `partition_handler_t` for each discovered partition.
- `partition.h:read_partition_block` - Reads eraseblocks/sectors from the underlying block or MTD device into `buf` during partition table scanning.
- `partition.h:struct partition_state_s` - Holds the active `struct inode` or `struct mtd_dev_s` reference along with block/eraseblock geometry (`blocksize`, `nblocks`, `erasesize`).
- `partition.h:parse_ptable_partition` - Parses legacy flash `PTABLE` partition headers.
- `partition.h:parse_gpt_partition` - Parses EFI GUID Partition Table (GPT) headers and partition entries.
- `partition.h:parse_mbr_partition` - Parses DOS Master Boot Record (MBR) primary and extended partition entries.
- `partition.h:parse_txtable_partition` - Parses TXTABLE partition entries.

## Invariants
- `fs_partition.c:parse_block_partition` and `fs_partition.c:parse_mtd_partition` require both the device reference (`ldev`/`mtd`) and `handler` callback to be non-NULL, returning `-EINVAL` otherwise.
- If no partition table signature matches on the medium, the parser emits a single fallback partition spanning the entire device (`firstblock = 0`, `nblocks = state.nblocks`) to `handler`.

## Side Effects
- Opens and closes block drivers (`open_blockdriver`, `close_blockdriver`), queries device geometry via `BDIOC_GEOMETRY` / `MTDIOC_GEOMETRY`, and reads raw sectors/blocks from storage (`BIP_READ`, `MTD_BREAD`).
- Invokes caller-supplied `partition_handler_t` callbacks which typically register sub-block or sub-MTD partition device nodes in `/dev`.

## Verification
- Run: `make test`
