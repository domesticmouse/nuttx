# inc (`nuttx/arch/arm/src/lpc43xx/spifi/inc`)

## Overview
Hardware abstraction and architecture package for `inc` under `nuttx/arch/arm/src/lpc43xx/spifi/inc`, providing 2 header file(s) and 0 source file(s) (including `spifilib_api.h`, `spifilib_dev.h`).

## Subdirectories & Boundaries
- `private`: [./private/README.md](./private/README.md) - Hardware abstraction and architecture package for `private` under `nuttx/arch/arm/src/lpc43xx/spifi/inc/private`, providing 1 header file(s) and 0 source file(s) (including `spifilib_chiphw.h`).

## Interface
- `[spifilib_api.h:spifiGetLibVersion]`
- `[spifilib_api.h:spifiInit]`
- `[spifilib_api.h:spifiRegisterFamily]`
- `[spifilib_api.h:spifiReturnErrString]`
- `[spifilib_api.h:spifiGetSuppFamilyCount]`
- `[spifilib_api.h:spifiGetSuppFamilyName]`
- `[spifilib_api.h:spifiGetHandleMemSize]`
- `[spifilib_api.h:spifiInitDevice]`
- `[spifilib_api.h:spifiDevSetOpts]`
- `[spifilib_api.h:spifiDevRegister]`
- `[spifilib_api.h:spifiDevEnumerateName]`
- `[spifilib_api.h:spifiDevInit]`
- `[spifilib_api.h:spifiDevDeInit]`
- `[spifilib_api.h:spifiDevSetMemMode]`
- `[spifilib_api.h:spifiDevGetMemoryMode]`
- `[spifilib_api.h:spifiDevGetInfo]`
- `[spifilib_api.h:spifiGetAddrFromBlock]`
- `[spifilib_api.h:spifiGetAddrFromSubBlock]`
- `[spifilib_api.h:spifiGetBlockFromAddr]`
- `[spifilib_api.h:spifiGetSubBlockFromAddr]`
- `[spifilib_api.h:spifiGetSubBlockFromBlock]`
- `[spifilib_api.h:spifiProgram]`
- `[spifilib_api.h:spifiRead]`
- `[spifilib_api.h:spifiErase]`
- `[spifilib_api.h:spifiEraseByAddr]`
- `[spifilib_api.h:spifiDevGetFamilyName]`
- `[spifilib_dev.h:SPIFI_ERR_T]`
- `[spifilib_dev.h:uint32_t]`
- `[spifilib_dev.h:spifi_REG_FAMILY_CommonCommandSet]`
- `[spifilib_dev.h:SPIFI_INFO_ID_T]`
- [./private/README.md](./private/README.md)

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
