# hardware (`nuttx/arch/arm/src/nuc1xx/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/nuc1xx/hardware`, providing 19 header file(s) and 0 source file(s) (including `nuc_adc.h`, `nuc_clk.h`, `nuc_cmp.h`, `nuc_config.h`).

## Interface
- `[nuc_clk.h:NUC_INTHI_FREQUENCY]`
- `[nuc_clk.h:NUC_INTLO_FREQUENCY]`
- `[nuc_clk.h:NUC_CLK_PWRCON_OFFSET]`
- `[nuc_clk.h:NUC_CLK_AHBCLK_OFFSET]`
- `[nuc_clk.h:NUC_CLK_APBCLK_OFFSET]`
- `[nuc_clk.h:NUC_CLK_CLKSTATUS_OFFSET]`
- `[nuc_clk.h:NUC_CLK_CLKSEL0_OFFSET]`
- `[nuc_clk.h:NUC_CLK_CLKSEL1_OFFSET]`
- `[nuc_clk.h:NUC_CLK_CLKSEL2_OFFSET]`
- `[nuc_clk.h:NUC_CLK_CLKDIV_OFFSET]`
- `[nuc_clk.h:NUC_CLK_PLLCON_OFFSET]`
- `[nuc_clk.h:NUC_CLK_FRQDIV_OFFSET]`
- `[nuc_config.h:NUC_CONFIG0_OFFSET]`
- `[nuc_config.h:NUC_CONFIG1_OFFSET]`
- `[nuc_config.h:NUC_CONFIG0]`
- `[nuc_config.h:NUC_CONFIG1]`
- `[nuc_config.h:CONFIG0_DFEN]`
- `[nuc_config.h:CONFIG0_LOCK]`
- `[nuc_config.h:CONFIG0_CBS]`
- `[nuc_config.h:CONFIG0_CBORST]`
- `[nuc_config.h:CONFIG0_CBOV_SHIFT]`
- `[nuc_config.h:CONFIG0_CBOV_MASK]`
- `[nuc_config.h:CONFIG0_CBOV_2p2V]`
- `[nuc_config.h:CONFIG0_CBOV_2p7V]`
- `[nuc_gcr.h:NUC_GCR_PDID_OFFSET]`
- `[nuc_gcr.h:NUC_GCR_RSTSRC_OFFSET]`
- `[nuc_gcr.h:NUC_GCR_IPRSTC1_OFFSET]`
- `[nuc_gcr.h:NUC_GCR_IPRSTC2_OFFSET]`
- `[nuc_gcr.h:NUC_GCR_CPR_OFFSET]`
- `[nuc_gcr.h:NUC_GCR_BODCR_OFFSET]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
