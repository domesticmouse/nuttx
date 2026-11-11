# hardware (`nuttx/arch/arm/src/nrf52/hardware`)

## Overview
Hardware abstraction and architecture package for `hardware` under `nuttx/arch/arm/src/nrf52/hardware`, providing 25 header file(s) and 0 source file(s) (including `nrf52_clock.h`, `nrf52_ficr.h`, `nrf52_gpio.h`, `nrf52_gpiote.h`).

## Interface
- `[nrf52_clock.h:HAVE_CLOCK_CALTIMER_EVENTS]`
- `[nrf52_clock.h:HAVE_CLOCK_HFXODEBOUNCE]`
- `[nrf52_clock.h:NRF52_CLOCK_TASKS_HFCLKSTART_OFFSET]`
- `[nrf52_clock.h:NRF52_CLOCK_TASKS_HFCLKSTOP_OFFSET]`
- `[nrf52_clock.h:NRF52_CLOCK_TASKS_LFCLKSTART_OFFSET]`
- `[nrf52_clock.h:NRF52_CLOCK_TASKS_LFCLKSTOP_OFFSET]`
- `[nrf52_clock.h:NRF52_CLOCK_TASKS_CAL_OFFSET]`
- `[nrf52_clock.h:NRF52_CLOCK_TASKS_CTSTART_OFFSET]`
- `[nrf52_clock.h:NRF52_CLOCK_TASKS_CTSTOP_OFFSET]`
- `[nrf52_clock.h:NRF52_CLOCK_EVENTS_HFCLKSTARTED_OFFSET]`
- `[nrf52_ficr.h:NRF52_FICR_CODEPAGESIZE_OFFSET]`
- `[nrf52_ficr.h:NRF52_FICR_CODESIZE_OFFSET]`
- `[nrf52_ficr.h:NRF52_FICR_DEVICEID0_OFFSET]`
- `[nrf52_ficr.h:NRF52_FICR_DEVICEID1_OFFSET]`
- `[nrf52_ficr.h:NRF52_FICR_ER0_OFFSET]`
- `[nrf52_ficr.h:NRF52_FICR_ER1_OFFSET]`
- `[nrf52_ficr.h:NRF52_FICR_ER2_OFFSET]`
- `[nrf52_ficr.h:NRF52_FICR_ER3_OFFSET]`
- `[nrf52_ficr.h:NRF52_FICR_IR0_OFFSET]`
- `[nrf52_ficr.h:NRF52_FICR_IR1_OFFSET]`
- `[nrf52_ficr.h:NRF52_FICR_IR2_OFFSET]`
- `[nrf52_ficr.h:NRF52_FICR_IR3_OFFSET]`
- `[nrf52_gpio.h:NRF52_GPIO_NPORTS]`
- `[nrf52_gpio.h:NRF52_GPIO_PORT0]`
- `[nrf52_gpio.h:NRF52_GPIO_PORT1]`
- `[nrf52_gpio.h:NRF52_GPIO_NPINS]`
- `[nrf52_gpio.h:NRF52_GPIO_OUT_OFFSET]`
- `[nrf52_gpio.h:NRF52_GPIO_OUTSET_OFFSET]`
- `[nrf52_gpio.h:NRF52_GPIO_OUTCLR_OFFSET]`
- `[nrf52_gpio.h:NRF52_GPIO_IN_OFFSET]`

## Invariants
- `[nrf52_clock.h:#error]` Compile-time guard: Unknown NRF52 chip !
- `[nrf52_radio.h:#error]` Compile-time guard: Unknown NRF52 chip !
- `[nrf52_uarte.h:#error]` Compile-time guard: Unknown NRF52 chip !
- `[nrf52_uicr.h:#error]` Compile-time guard: Unknown NRF52 chip !

## Side Effects
- `[nrf52_utils.h:putreg32]` Writes 32-bit values directly to memory-mapped I/O (MMIO) peripheral registers

## Verification
- Run: `make test`
