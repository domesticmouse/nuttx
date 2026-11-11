# hardware (`nuttx/arch/risc-v/src/mpfs/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/risc-v/src/mpfs/hardware`, providing 26 header file(s) and 0 source file(s) (including `mpfs250t_484_pinmap.h`, `mpfs_cache.h`, `mpfs_can.h`, `mpfs_clint.h`).

## Interface
- `[mpfs250t_484_pinmap.h:MSSIO_AF_SDIO]`
- `[mpfs250t_484_pinmap.h:MSSIO_AF_EMMC]`
- `[mpfs250t_484_pinmap.h:MSSIO_AF_QSPI]`
- `[mpfs250t_484_pinmap.h:MSSIO_AF_SPI]`
- `[mpfs250t_484_pinmap.h:MSSIO_AF_USB]`
- `[mpfs250t_484_pinmap.h:MSSIO_AF_MMUART]`
- `[mpfs250t_484_pinmap.h:MSSIO_AF_I2C]`
- `[mpfs250t_484_pinmap.h:MSSIO_AF_CAN]`
- `[mpfs250t_484_pinmap.h:MSSIO_AF_MDIO]`
- `[mpfs250t_484_pinmap.h:MSSIO_AF_MISC]`
- `[mpfs250t_484_pinmap.h:MSSIO_AF_RSVD]`
- `[mpfs250t_484_pinmap.h:MSSIO_AF_GPIO]`
- `[mpfs_cache.h:MPFS_CACHE_CTRL_BASE]`
- `[mpfs_cache.h:MPFS_CACHE_CONFIG_OFFSET]`
- `[mpfs_cache.h:MPFS_CACHE_WAY_ENABLE_OFFSET]`
- `[mpfs_cache.h:MPFS_CACHE_ECC_INJECT_ERROR_OFFSET]`
- `[mpfs_cache.h:MPFS_CACHE_ECC_DIR_FIX_ADDR_OFFSET]`
- `[mpfs_cache.h:MPFS_CACHE_ECC_DIR_FIX_COUNT_OFFSET]`
- `[mpfs_cache.h:MPFS_CACHE_ECC_DATA_FIX_ADDR_OFFSET]`
- `[mpfs_cache.h:MPFS_CACHE_ECC_DATA_FIX_COUNT_OFFSET]`
- `[mpfs_cache.h:MPFS_CACHE_ECC_DATA_FAIL_ADDR_OFFSET]`
- `[mpfs_cache.h:MPFS_CACHE_ECC_DATA_FAIL_COUNT_OFFSET]`
- `[mpfs_cache.h:MPFS_CACHE_FLUSH64_OFFSET]`
- `[mpfs_cache.h:MPFS_CACHE_FLUSH32_OFFSET]`
- `[mpfs_can.h:MPFS_CAN_INT_STATUS_OFFSET]`
- `[mpfs_can.h:MPFS_CAN_INT_ENABLE_OFFSET]`
- `[mpfs_can.h:MPFS_CAN_RX_BUF_STATUS_OFFSET]`
- `[mpfs_can.h:MPFS_CAN_TX_BUF_STATUS_OFFSET]`
- `[mpfs_can.h:MPFS_CAN_ERROR_STATUS_OFFSET]`
- `[mpfs_can.h:MPFS_CAN_CAN_COMMAND_OFFSET]`

## Invariants
- `[mpfs_gpio.h:#error]` Compile-time guard: The selected MPFS variant is not implemented
- `[mpfs_ihc.h:#error]` Compile-time guard: Harts misconfigured. Cannot use the same harts.

## Side Effects
- None

## Verification
- Run: `make test`
