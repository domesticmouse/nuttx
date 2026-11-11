# hardware (`nuttx/arch/arm/src/nrf91/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/nrf91/hardware`, providing 18 header file(s) and 0 source file(s) (including `nrf91_clock.h`, `nrf91_ficr.h`, `nrf91_gpio.h`, `nrf91_gpiote.h`).

## Interface
- `[nrf91_clock.h:NRF91_CLOCK_TASKS_HFCLKSTART_OFFSET]`
- `[nrf91_clock.h:NRF91_CLOCK_TASKS_HFCLKSTOP_OFFSET]`
- `[nrf91_clock.h:NRF91_CLOCK_TASKS_LFCLKSTART_OFFSET]`
- `[nrf91_clock.h:NRF91_CLOCK_TASKS_LFCLKSTOP_OFFSET]`
- `[nrf91_clock.h:NRF91_CLOCK_EVENTS_HFCLKSTARTED_OFFSET]`
- `[nrf91_clock.h:NRF91_CLOCK_EVENTS_LFCLKSTARTED_OFFSET]`
- `[nrf91_clock.h:NRF91_CLOCK_INTENSET_OFFSET]`
- `[nrf91_clock.h:NRF91_CLOCK_INTENCLR_OFFSET]`
- `[nrf91_clock.h:NRF91_CLOCK_HFCLKRUN_OFFSET]`
- `[nrf91_clock.h:NRF91_CLOCK_HFCLKSTAT_OFFSET]`
- `[nrf91_clock.h:NRF91_CLOCK_LFCLKRUN_OFFSET]`
- `[nrf91_clock.h:NRF91_CLOCK_LFCLKSTAT_OFFSET]`
- `[nrf91_ficr.h:NRF91_FICR_INFO_DEVICEID0_OFFSET]`
- `[nrf91_ficr.h:NRF91_FICR_INFO_DEVICEID1_OFFSET]`
- `[nrf91_ficr.h:NRF91_FICR_INFO_RAM_OFFSET]`
- `[nrf91_ficr.h:NRF91_FICR_INFO_FLASH_OFFSET]`
- `[nrf91_ficr.h:NRF91_FICR_INFO_CODEPAGESIZE_OFFSET]`
- `[nrf91_ficr.h:NRF91_FICR_INFO_CODESIZE_OFFSET]`
- `[nrf91_ficr.h:NRF91_FICR_INFO_DEVICETYPE_OFFSET]`
- `[nrf91_ficr.h:NRF91_FICR_LAST_OFFSET]`
- `[nrf91_ficr.h:NRF91_FICR_INFO_DEVICEID0]`
- `[nrf91_ficr.h:NRF91_FICR_INFO_DEVICEID1]`
- `[nrf91_ficr.h:NRF91_FICR_INFO_RAM]`
- `[nrf91_ficr.h:NRF91_FICR_INFO_FLASH]`
- `[nrf91_gpio.h:NRF91_GPIO_NPORTS]`
- `[nrf91_gpio.h:NRF91_GPIO_PORT0]`
- `[nrf91_gpio.h:NRF91_GPIO_NPINS]`
- `[nrf91_gpio.h:NRF91_GPIO_OUT_OFFSET]`
- `[nrf91_gpio.h:NRF91_GPIO_OUTSET_OFFSET]`
- `[nrf91_gpio.h:NRF91_GPIO_OUTCLR_OFFSET]`

## Invariants
- None

## Side Effects
- `[nrf91_utils.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers

## Verification
- Run: `make test`
