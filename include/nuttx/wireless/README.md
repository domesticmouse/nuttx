# NuttX Wireless & Radio Subsystem (`include/nuttx/wireless`)

## Overview
Provides top-level wireless network and character radio abstractions (`wireless.h`, `ioctl.h`, `pktradio.h`), proprietary sub-GHz/2.4GHz packet radio and Wi-Fi transceiver interfaces (TI CC1101, Nordic nRF24L01, ST SPIRIT1, Telit GS2200M, Morse Micro), and organizes protocol-specific subdirectories for Bluetooth, Cellular, IEEE 802.11, IEEE 802.15.4, LPWAN, and LTE.

## Interface
- `wireless.h:iwreq`, `wireless.h:iwreq_data`, `wireless.h:iw_point`, `wireless.h:iw_freq`, `wireless.h:iw_quality`, `wireless.h:iw_range`, `wireless.h:SIOCSIWFREQ`, `wireless.h:SIOCGIWFREQ`, `wireless.h:SIOCSIWMODE`, `wireless.h:SIOCGIWMODE`, `wireless.h:SIOCSIWESSID`, `wireless.h:SIOCGIWESSID` - Linux Wireless Extensions (`WEXT`) compatible socket `ioctl` commands and data structures.
- `ioctl.h:wlioc_modulation_e`, `ioctl.h:wlioc_lora_cr_e`, `ioctl.h:wlioc_rx_hdr_s`, `ioctl.h:WLIOC_SETRADIOFREQ`, `ioctl.h:WLIOC_GETRADIOFREQ`, `ioctl.h:WLIOC_SETTXPOWER`, `ioctl.h:WLIOC_GETTXPOWER`, `ioctl.h:WLIOC_SETMODU` - Character-driver wireless radio `ioctl` commands (`WLIOC_*`).
- `pktradio.h:pktradio_addr_s`, `pktradio.h:pktradio_properties_s`, `pktradio.h:pktradio_ifreq_s`, `pktradio.h:pktradio_metadata_s`, `pktradio.h:pktradio_metadata_initialize`, `pktradio.h:pktradio_metadata_allocate`, `pktradio.h:pktradio_metadata_free`, `pktradio.h:pktradio_loopback` - Non-IEEE 802.15.4 6LoWPAN packet radio network adapter and metadata pool.
- Transceiver Drivers: `cc1101.h:cc1101_dev_s`, `cc1101.h:cc1101_init`, `cc1101.h:cc1101_send`, `nrf24l01.h:nrf24l01_config_s`, `nrf24l01.h:nrf24l01_register`, `spirit.h:spirit_lower_s`, `spirit.h:spirit_netdev_initialize`, `gs2200m.h:gs2200m_lower_s`, `gs2200m.h:gs2200m_register`, `morse.h:morse_lower_s`, `morse.h:morse_register`.
- Subdirectories:
  - [./bluetooth/README.md](./bluetooth/README.md) - Bluetooth & BLE HCI, GATT, UUID, buffer, and transport driver interfaces.
  - [./cellular/README.md](./cellular/README.md) - Cellular network device `ioctl` commands and request structures.
  - [./ieee80211/README.md](./ieee80211/README.md) - IEEE 802.11 MAC headers, crypto suites, and Broadcom FullMAC (`bcmf`) SDIO/gSPI drivers.
  - [./ieee802154/README.md](./ieee802154/README.md) - IEEE 802.15.4 MAC, radio lower-half, and MRF24J40/AT86RF23x/XBee transceiver interfaces.
  - [./lpwan/README.md](./lpwan/README.md) - LoRa and LPWAN transceiver/gateway interfaces (SX126x, SX127x, SX1301, RN2xx3).
  - [./lte/README.md](./lte/README.md) - LTE cellular modem control structures and `SIOCLTECMD` `ioctl` commands.

## Invariants
- Device-specific character radio `ioctl` commands must start at or above `ioctl.h:WLIOC_USER` so they do not collide with common `WLIOC_*` commands (`WLIOC_SETRADIOFREQ`..`WLIOC_GETOOKBITRATE`).
- `pktradio.h:pktradio_metadata_initialize` must be called once before allocating frame metadata structures via `pktradio.h:pktradio_metadata_allocate`.

## Side Effects
- Registering wireless drivers (`nrf24l01.h:nrf24l01_register`, `gs2200m.h:gs2200m_register`, `spirit.h:spirit_netdev_initialize`, `morse.h:morse_register`) initializes SPI/GPIO hardware, attaches interrupt handlers, and registers `/dev/nrf24l01`, `/dev/gs2200m`, or network interfaces.

## Verification
- Run: `make test`
