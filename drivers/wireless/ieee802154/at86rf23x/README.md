# Atmel AT86RF23x IEEE 802.15.4 Radio Driver (`drivers/wireless/ieee802154/at86rf23x`)

## Overview
Implements the IEEE 802.15.4 radio lower-half driver (`struct ieee802154_radio_s`) for Atmel AT86RF231/AT86RF233 2.4 GHz SPI transceivers (`at86rf23x.c`, `at86rf23x.h`).

## Interface
- `[at86rf23x.c:at86rf23x_init]` - Allocates and initializes an AT86RF23x radio device instance (`struct ieee802154_radio_s`) over SPI and attaches its IRQ handler.
- `[at86rf23x.h:RF23X_SPI_REG_READ]`, `[at86rf23x.h:RF23X_SPI_REG_WRITE]`, `[at86rf23x.h:RF23X_SPI_FRAME_READ]`, `[at86rf23x.h:RF23X_SPI_FRAME_WRITE]`, `[at86rf23x.h:RF23X_SPI_SRAM_READ]`, `[at86rf23x.h:RF23X_SPI_SRAM_WRITE]` - SPI command header and register bitfield definitions for AT86RF23x transceivers.

## Invariants
- `[at86rf23x.c:at86rf23x_interrupt]` asserts `DEBUGASSERT(dev != NULL)` and `DEBUGASSERT(work_available(&dev->irqwork))` before queuing interrupt work.

## Side Effects
- Toggles hardware RESET and SLP_TR pins via `dev->lower->reset` and `dev->lower->slptr`, locks the SPI bus (`SPI_LOCK`), and performs register and frame buffer SPI transfers (`SPI_SEND`, `SPI_SNDBLOCK`, `SPI_RECVBLOCK`).
- Attaches the transceiver IRQ (`lower->attach`) and schedules interrupt handling on `HPWORK` (`work_queue`).

## Verification
- Run: `make test`
