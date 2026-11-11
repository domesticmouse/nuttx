# src (`nuttx/arch/arm/src/lpc43xx/spifi/src`)

## Overview
Hardware abstraction and architecture package for `src` under `nuttx/arch/arm/src/lpc43xx/spifi/src`, providing 0 header file(s) and 2 source file(s) (including `spifilib_dev_common.c`, `spifilib_fam_standard_cmd.c`).

## Interface
- `[spifilib_dev_common.c:spifiRegisterFamily]`
- `[spifilib_dev_common.c:spifiDevRegister]`
- `[spifilib_dev_common.c:spifiDevEnumerateName]`
- `[spifilib_dev_common.c:spifiGetLibVersion]`
- `[spifilib_dev_common.c:spifiInit]`
- `[spifilib_dev_common.c:spifiDevInit]`
- `[spifilib_dev_common.c:spifiDevDeInit]`
- `[spifilib_dev_common.c:spifiReturnErrString]`
- `[spifilib_dev_common.c:spifiDevGetInfo]`
- `[spifilib_dev_common.c:spifiDevGetMemoryMode]`
- `[spifilib_dev_common.c:spifiDevSetMemMode]`
- `[spifilib_dev_common.c:spifiGetSuppFamilyCount]`
- `[spifilib_dev_common.c:spifiGetSuppFamilyName]`
- `[spifilib_dev_common.c:spifiGetHandleMemSize]`
- `[spifilib_dev_common.c:spifiInitDevice]`
- `[spifilib_dev_common.c:spifiDevSetOpts]`
- `[spifilib_dev_common.c:spifiGetAddrFromBlock]`
- `[spifilib_dev_common.c:spifiGetAddrFromSubBlock]`
- `[spifilib_dev_common.c:spifiGetBlockFromAddr]`
- `[spifilib_dev_common.c:spifiGetSubBlockFromAddr]`
- `[spifilib_dev_common.c:spifiGetSubBlockFromBlock]`
- `[spifilib_dev_common.c:spifiProgram]`
- `[spifilib_dev_common.c:spifiRead]`
- `[spifilib_dev_common.c:spifiErase]`
- `[spifilib_dev_common.c:spifiEraseByAddr]`
- `[spifilib_fam_standard_cmd.c:spifi_REG_FAMILY_CommonCommandSet]`
- `[Make.defs:CHIP_CSRCS]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
