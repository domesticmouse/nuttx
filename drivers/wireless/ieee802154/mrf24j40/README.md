# Microchip MRF24J40 IEEE 802.15.4 Radio Driver (`drivers/wireless/ieee802154/mrf24j40`)

## Overview
Implements the IEEE 802.15.4 radio lower-half driver (`struct ieee802154_radio_s`) for the Microchip MRF24J40 2.4 GHz transceiver over SPI, including short/long address register access (`mrf24j40_regops.c`), radio attribute configuration (`mrf24j40_getset.c`), interrupt and FIFO handling (`mrf24j40_interrupt.c`), and MAC-to-radio interface operations (`mrf24j40_radif.c`, `mrf24j40.c`).

## Interface
- `[mrf24j40.c:mrf24j40_init]` - Initializes the MRF24J40 SPI transceiver and returns its `struct ieee802154_radio_s` interface.
- `[mrf24j40.c:mrf24j40_dopoll_csma]`, `[mrf24j40.c:mrf24j40_dopoll_gts]`, `[mrf24j40.c:mrf24j40_norm_setup]`, `[mrf24j40.c:mrf24j40_norm_trigger]`, `[mrf24j40.c:mrf24j40_beacon_setup]`, `[mrf24j40.c:mrf24j40_beacon_trigger]`, `[mrf24j40.c:mrf24j40_gts_setup]`, `[mrf24j40.c:mrf24j40_setup_fifo]` - Normal CSMA, beacon, and GTS FIFO setup and transmission trigger routines.
- `[mrf24j40_radif.c:mrf24j40_bind]`, `[mrf24j40_radif.c:mrf24j40_reset]`, `[mrf24j40_radif.c:mrf24j40_getattr]`, `[mrf24j40_radif.c:mrf24j40_setattr]`, `[mrf24j40_radif.c:mrf24j40_txnotify]`, `[mrf24j40_radif.c:mrf24j40_txdelayed]`, `[mrf24j40_radif.c:mrf24j40_rxenable]`, `[mrf24j40_radif.c:mrf24j40_energydetect]`, `[mrf24j40_radif.c:mrf24j40_beaconstart]`, `[mrf24j40_radif.c:mrf24j40_beaconupdate]`, `[mrf24j40_radif.c:mrf24j40_beaconstop]`, `[mrf24j40_radif.c:mrf24j40_sfupdate]` - IEEE 802.15.4 radio interface methods.
- `[mrf24j40_getset.c:mrf24j40_setrxmode]`, `[mrf24j40_getset.c:mrf24j40_setchannel]`, `[mrf24j40_getset.c:mrf24j40_setpanid]`, `[mrf24j40_getset.c:mrf24j40_setsaddr]`, `[mrf24j40_getset.c:mrf24j40_seteaddr]`, `[mrf24j40_getset.c:mrf24j40_setcoordsaddr]`, `[mrf24j40_getset.c:mrf24j40_setcoordeaddr]`, `[mrf24j40_getset.c:mrf24j40_setdevmode]`, `[mrf24j40_getset.c:mrf24j40_settxpower]`, `[mrf24j40_getset.c:mrf24j40_setcca]` - Hardware filter, channel, TX power, and CCA configuration helpers.
- `[mrf24j40_regops.c:mrf24j40_setreg]`, `[mrf24j40_regops.c:mrf24j40_getreg]`, `[mrf24j40_regops.c:mrf24j40_regdump]` - 6-bit short-address and 10-bit long-address SPI register accessors.
- `[mrf24j40_interrupt.c:mrf24j40_interrupt]`, `[mrf24j40_interrupt.c:mrf24j40_irqworker]` - Interrupt handler and `HPWORK` deferred worker.

## Invariants
- `[mrf24j40_interrupt.c:mrf24j40_interrupt]` and `[mrf24j40_radif.c:mrf24j40_txdelayed]` assert `DEBUGASSERT(dev != NULL)`, `DEBUGASSERT(dev->spi)`, and `DEBUGASSERT(!dev->txdelayed_busy)`.

## Side Effects
- Locks the SPI bus (`SPI_LOCK`) and performs SPI register/FIFO transfers (`SPI_SEND`, `SPI_SNDBLOCK`, `SPI_RECVBLOCK`) under `nxmutex_lock(&dev->lock)`.
- Attaches hardware IRQ via `dev->lower->attach`, schedules `mrf24j40_irqworker` on `HPWORK` (`work_queue`), and notifies the bound IEEE 802.15.4 MAC layer of RX frames and TX completions.

## Verification
- Run: `make test`
