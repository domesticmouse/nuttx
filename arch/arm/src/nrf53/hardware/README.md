# hardware (`nuttx/arch/arm/src/nrf53/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/nrf53/hardware`, providing 37 header file(s) and 0 source file(s) (including `nrf53_cache.h`, `nrf53_clock.h`, `nrf53_ctrlap.h`, `nrf53_dppi.h`).

## Interface
- `[nrf53_cache.h:NRF53_CACHE_ENABLE_OFFSET]`
- `[nrf53_cache.h:NRF53_CACHE_INVALIDATE_OFFSET]`
- `[nrf53_cache.h:NRF53_CACHE_INFO_OFFSET]`
- `[nrf53_cache.h:NRF53_CACHE_PROFILINGENABLE_OFFSET]`
- `[nrf53_cache.h:NRF53_CACHE_MODE_OFFSET]`
- `[nrf53_cache.h:NRF53_CACHE_ENABLE]`
- `[nrf53_cache.h:NRF53_CACHE_INVALIDATE]`
- `[nrf53_cache.h:NRF53_CACHE_INFO]`
- `[nrf53_cache.h:NRF53_CACHE_PROFILINGENABLE]`
- `[nrf53_cache.h:NRF53_CACHE_MODE]`
- `[nrf53_cache.h:CACHE_ENABLE_ENABLE]`
- `[nrf53_cache.h:CACHE_INVALIDATE_INVALIDATE]`
- `[nrf53_clock.h:NRF53_CLOCK_TASKS_HFCLKSTART_OFFSET]`
- `[nrf53_clock.h:NRF53_CLOCK_TASKS_HFCLKSTOP_OFFSET]`
- `[nrf53_clock.h:NRF53_CLOCK_TASKS_LFCLKSTART_OFFSET]`
- `[nrf53_clock.h:NRF53_CLOCK_TASKS_LFCLKSTOP_OFFSET]`
- `[nrf53_clock.h:NRF53_CLOCK_TASKS_CAL_OFFSET]`
- `[nrf53_clock.h:NRF53_CLOCK_TASKS_HFCLKAUDIOSTART_OFFSET]`
- `[nrf53_clock.h:NRF53_CLOCK_TASKS_HFCLKAUDIOSTOP_OFFSET]`
- `[nrf53_clock.h:NRF53_CLOCK_TASKS_HFCLK192MSTART_OFFSET]`
- `[nrf53_clock.h:NRF53_CLOCK_TASKS_HFCLK192MSTOP_OFFSET]`
- `[nrf53_clock.h:NRF53_CLOCK_EVENTS_HFCLKSTARTED_OFFSET]`
- `[nrf53_clock.h:NRF53_CLOCK_EVENTS_LFCLKSTARTED_OFFSET]`
- `[nrf53_clock.h:NRF53_CLOCK_EVENTS_DONE_OFFSET]`
- `[nrf53_ctrlap.h:NRF53_CTRLAP_MAILBOXRXDATA_OFFSET]`
- `[nrf53_ctrlap.h:NRF53_CTRLAP_MAILBOXRXSTATUS_OFFSET]`
- `[nrf53_ctrlap.h:NRF53_CTRLAP_MAILBOXTXDATA_OFFSET]`
- `[nrf53_ctrlap.h:NRF53_CTRLAP_MAILBOXTXSTATUS_OFFSET]`
- `[nrf53_ctrlap.h:NRF53_CTRLAP_ERASEPROTECTLOCK_OFFSET]`
- `[nrf53_ctrlap.h:NRF53_CTRLAP_ERASEPROTECTDISABLE_OFFSET]`

## Invariants
- `[nrf53_memorymap.h:#error]` Compile-time guard: Unsupported NRF5340 CPU
- `[nrf53_radio.h:#error]` Compile-time guard: RADIO is available only on the nRF5340 network core

## Side Effects
- `[nrf53_utils.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers

## Verification
- Run: `make test`
