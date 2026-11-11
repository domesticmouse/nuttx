# hardware (`nuttx/arch/arm/src/samd5e5/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/samd5e5/hardware`, providing 29 header file(s) and 0 source file(s) (including `sam_aes.h`, `sam_cmcc.h`, `sam_dmac.h`, `sam_eic.h`).

## Interface
- `[sam_aes.h:SAM_AES_CTRLA_OFFSET]`
- `[sam_aes.h:SAM_AES_CTRLB_OFFSET]`
- `[sam_aes.h:SAM_AES_INTENCLR_OFFSET]`
- `[sam_aes.h:SAM_AES_INTENSET_OFFSET]`
- `[sam_aes.h:SAM_AES_INTENFLAG_OFFSET]`
- `[sam_aes.h:SAM_AES_DATABUFPTR_OFFSET]`
- `[sam_aes.h:SAM_AES_DBGCTRL_OFFSET]`
- `[sam_aes.h:SAM_AES_KEYWORD_OFFSET]`
- `[sam_aes.h:SAM_AES_KEYWORD0_OFFSET]`
- `[sam_aes.h:SAM_AES_KEYWORD1_OFFSET]`
- `[sam_aes.h:SAM_AES_KEYWORD2_OFFSET]`
- `[sam_aes.h:SAM_AES_KEYWORD3_OFFSET]`
- `[sam_cmcc.h:CMCC_CACHE_SIZE]`
- `[sam_cmcc.h:CMCC_CACHE_LINE_SIZE]`
- `[sam_cmcc.h:CMCC_NWAYS]`
- `[sam_cmcc.h:SAM_CMCC_TYPE_OFFSET]`
- `[sam_cmcc.h:SAM_CMCC_CFG_OFFSET]`
- `[sam_cmcc.h:SAM_CMCC_CTRL_OFFSET]`
- `[sam_cmcc.h:SAM_CMCC_SR_OFFSET]`
- `[sam_cmcc.h:SAM_CMCC_LCKWAY_OFFSET]`
- `[sam_cmcc.h:SAM_CMCC_MAINT0_OFFSET]`
- `[sam_cmcc.h:SAM_CMCC_MAINT1_OFFSET]`
- `[sam_cmcc.h:SAM_CMCC_MCFG_OFFSET]`
- `[sam_cmcc.h:SAM_CMCC_MEN_OFFSET]`
- `[sam_dmac.h:dma_desc_s]`
- `[sam_dmac.h:SAM_DMAC_CTRL_OFFSET]`
- `[sam_dmac.h:SAM_DMAC_CRCCTRL_OFFSET]`
- `[sam_dmac.h:SAM_DMAC_CRCDATAIN_OFFSET]`
- `[sam_dmac.h:SAM_DMAC_CRCCHKSUM_OFFSET]`
- `[sam_dmac.h:SAM_DMAC_CRCSTATUS_OFFSET]`

## Invariants
- `[sam_memorymap.h:#error]` Compile-time guard: Unsupported SAMD5/E5 family
- `[sam_pinmap.h:#error]` Compile-time guard: Unsupported SAMD5/E5 family

## Side Effects
- None

## Verification
- Run: `make test`
