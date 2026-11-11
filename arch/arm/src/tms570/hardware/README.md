# hardware (`nuttx/arch/arm/src/tms570/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/tms570/hardware`, providing 15 header file(s) and 0 source file(s) (including `tms570_esm.h`, `tms570_flash.h`, `tms570_gio.h`, `tms570_iomm.h`).

## Interface
- `[tms570_esm.h:ESM_GROUP1]`
- `[tms570_esm.h:ESM_GROUP2]`
- `[tms570_esm.h:ESM_GROUP3]`
- `[tms570_esm.h:TMS570_ESM_EEPAPR1_OFFSET]`
- `[tms570_esm.h:TMS570_ESM_DEPAPR1_OFFSET]`
- `[tms570_esm.h:TMS570_ESM_IESR1_OFFSET]`
- `[tms570_esm.h:TMS570_ESM_IECR1_OFFSET]`
- `[tms570_esm.h:TMS570_ESM_ILSR1_OFFSET]`
- `[tms570_esm.h:TMS570_ESM_ILCR1_OFFSET]`
- `[tms570_esm.h:TMS570_ESM_SRA_OFFSET]`
- `[tms570_esm.h:TMS570_ESM_SR1_OFFSET]`
- `[tms570_esm.h:TMS570_ESM_SR2_OFFSET]`
- `[tms570_flash.h:TMS570_FLASH_FRDCNTL_OFFSET]`
- `[tms570_flash.h:TMS570_FLASH_FEDACTRL1_OFFSET]`
- `[tms570_flash.h:TMS570_FLASH_FEDACTRL2_OFFSET]`
- `[tms570_flash.h:TMS570_FLASH_FCORERRCNT_OFFSET]`
- `[tms570_flash.h:TMS570_FLASH_FCORERRADD_OFFSET]`
- `[tms570_flash.h:TMS570_FLASH_FCORERRPOS_OFFSET]`
- `[tms570_flash.h:TMS570_FLASH_FEDACSTATUS_OFFSET]`
- `[tms570_flash.h:TMS570_FLASH_FUNCERRADD_OFFSET]`
- `[tms570_flash.h:TMS570_FLASH_FEDACSDIS_OFFSET]`
- `[tms570_flash.h:TMS570_FLASH_FPRIMADDTAG_OFFSET]`
- `[tms570_flash.h:TMS570_FLASH_FDUPDDTAG_OFFSET]`
- `[tms570_flash.h:TMS570_FLASH_FBPROT_OFFSET]`
- `[tms570_gio.h:TMS570_GIOA]`
- `[tms570_gio.h:TMS570_GIOB]`
- `[tms570_gio.h:TMS570_GIOC]`
- `[tms570_gio.h:TMS570_GIOD]`
- `[tms570_gio.h:TMS570_GIOE]`
- `[tms570_gio.h:TMS570_GIOF]`

## Invariants
- `[tms570_memorymap.h:#error]` Compile-time guard: No memory map for the TMS570LS0232PZ
- `[tms570_pinmux.h:#error]` Compile-time guard: No pin multiplexing for the TMS570LS0232PZ

## Side Effects
- None

## Verification
- Run: `make test`
