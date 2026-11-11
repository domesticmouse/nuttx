# Digi XBee IEEE 802.15.4 Driver (`drivers/wireless/ieee802154/xbee`)

## Overview
Implements the SPI driver, AT/API frame protocol engine (`xbee.c`), MAC layer interface (`xbee_mac.c`, `xbee_ioctl.c`), and 6LoWPAN/IEEE 802.15.4 network device wrapper (`xbee_netdev.c`) for Digi XBee S1 IEEE 802.15.4 radio modules.

## Interface
- `[xbee.c:xbee_init]`, `[xbee.c:xbee_send_apiframe]`, `[xbee.c:xbee_atquery]`, `[xbee.c:xbee_send_atquery]`, `[xbee.c:xbee_set_panid]`, `[xbee.c:xbee_set_saddr]`, `[xbee.c:xbee_set_eaddr]`, `[xbee.c:xbee_set_chan]`, `[xbee.c:xbee_set_powerlevel]`, `[xbee.c:xbee_set_epassocflags]`, `[xbee.c:xbee_set_coordassocflags]`, `[xbee.c:xbee_enable_coord]`, `[xbee.c:xbee_regdump]` - Initializes the XBee SPI radio instance and sends API frames and AT configuration commands.
- `[xbee_mac.c:xbee_bind]`, `[xbee_mac.c:xbee_get_mhrlen]`, `[xbee_mac.c:xbee_req_data]`, `[xbee_mac.c:xbee_req_get]`, `[xbee_mac.c:xbee_req_set]`, `[xbee_mac.c:xbee_req_start]`, `[xbee_mac.c:xbee_req_associate]`, `[xbee_mac.c:xbee_req_reset]`, `[xbee_ioctl.c:xbee_ioctl]` - IEEE 802.15.4 MAC callback binding, primitive requests, and `ioctl` dispatch.
- `[xbee_netdev.c:xbee_netdev_register]` - Registers the XBee MAC handle as a NuttX IEEE 802.15.4 / 6LoWPAN network device (`wpanN`).

## Invariants
- `[xbee.c:xbee_init]` and SPI helpers assert `DEBUGASSERT(priv != NULL)` and `DEBUGASSERT(priv->spi)`.
- `[xbee.h:xbee_insert_framedata]` asserts `DEBUGASSERT(framelen > XBEE_APIFRAME_OVERHEAD)`.
- `[xbee_netdev.c:xbee_netdev_register]` callbacks assert `DEBUGASSERT(dev != NULL && dev->d_private != NULL)`.

## Side Effects
- Acquires the SPI bus (`SPI_LOCK`), toggles XBee chip-select (`SPI_SELECT`), and exchanges API frames via `SPI_SNDBLOCK` / `SPI_RECVBLOCK` / `SPI_SEND`.
- Attaches ATTN pin interrupts via `lower->attach`, schedules RX/TX/association work on `HPWORK` and `LPWORK` (`work_queue`), and registers a network device via `netdev_register`.

## Verification
- Run: `make test`
