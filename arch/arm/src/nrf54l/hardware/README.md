# hardware (`nuttx/arch/arm/src/nrf54l/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/nrf54l/hardware`, providing 23 header file(s) and 0 source file(s) (including `nrf54l_cache.h`, `nrf54l_clock.h`, `nrf54l_dppic.h`, `nrf54l_ficr.h`).

## Interface
- `[nrf54l_cache.h:NRF54L_CACHE_TASKS_INVALIDATECACHE_OFFSET]`
- `[nrf54l_cache.h:NRF54L_CACHE_TASKS_INVALIDATELINE_OFFSET]`
- `[nrf54l_cache.h:NRF54L_CACHE_TASKS_ERASE_OFFSET]`
- `[nrf54l_cache.h:NRF54L_CACHE_STATUS_OFFSET]`
- `[nrf54l_cache.h:NRF54L_CACHE_ENABLE_OFFSET]`
- `[nrf54l_cache.h:NRF54L_CACHE_LINEADDR_OFFSET]`
- `[nrf54l_cache.h:NRF54L_CACHE_PROFILING_ENABLE_OFFSET]`
- `[nrf54l_cache.h:NRF54L_CACHE_PROFILING_HIT_OFFSET]`
- `[nrf54l_cache.h:NRF54L_CACHE_PROFILING_MISS_OFFSET]`
- `[nrf54l_cache.h:NRF54L_CACHE_PROFILING_LMISS_OFFSET]`
- `[nrf54l_cache.h:NRF54L_CACHE_PROFILING_READS_OFFSET]`
- `[nrf54l_cache.h:NRF54L_CACHE_PROFILING_WRITES_OFFSET]`
- `[nrf54l_clock.h:NRF54L_CLOCK_TASKS_XOSTART_OFFSET]`
- `[nrf54l_clock.h:NRF54L_CLOCK_TASKS_XOSTOP_OFFSET]`
- `[nrf54l_clock.h:NRF54L_CLOCK_TASKS_PLLSTART_OFFSET]`
- `[nrf54l_clock.h:NRF54L_CLOCK_TASKS_PLLSTOP_OFFSET]`
- `[nrf54l_clock.h:NRF54L_CLOCK_TASKS_LFCLKSTART_OFFSET]`
- `[nrf54l_clock.h:NRF54L_CLOCK_TASKS_LFCLKSTOP_OFFSET]`
- `[nrf54l_clock.h:NRF54L_CLOCK_TASKS_CAL_OFFSET]`
- `[nrf54l_clock.h:NRF54L_CLOCK_TASKS_XOTUNE_OFFSET]`
- `[nrf54l_clock.h:NRF54L_CLOCK_TASKS_XOTUNEABORT_OFFSET]`
- `[nrf54l_clock.h:NRF54L_CLOCK_TASKS_XO24MSTART_OFFSET]`
- `[nrf54l_clock.h:NRF54L_CLOCK_TASKS_XO24MSTOP_OFFSET]`
- `[nrf54l_clock.h:NRF54L_CLOCK_SUBSCRIBE_XOSTART_OFFSET]`
- `[nrf54l_dppic.h:NRF54L_DPPIC_CHEN_OFFSET]`
- `[nrf54l_dppic.h:NRF54L_DPPIC_CHENSET_OFFSET]`
- `[nrf54l_dppic.h:NRF54L_DPPIC_CHENCLR_OFFSET]`
- `[nrf54l_dppic.h:DPPIC_CHEN_CH]`
- `[nrf54l_dppic.h:DPPI_CHIDX_SHIFT]`
- `[nrf54l_dppic.h:DPPI_CHIDX_MASK]`

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
