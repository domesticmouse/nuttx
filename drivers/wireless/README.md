# Wireless Transceiver and Network Drivers (`drivers/wireless`)

## Overview
Provides standalone SPI wireless drivers for the Texas Instruments CC1101 sub-1 GHz RF transceiver (`cc1101.c` and ISM band RF settings tables `ISM1_868MHzGFSK100kbps.c`, `ISM2_433MHzMSK500kbps.c`, `ISM2_905MHzGFSK250kbps.c`), GainSpan GS2200M Wi-Fi module (`gs2200m.c`), and Nordic Semiconductor nRF24L01 2.4 GHz transceiver (`nrf24l01.c`), and groups the Bluetooth, IEEE 802.11, IEEE 802.15.4, LPWAN, and ST SPIRIT1 wireless driver subsystems.

## Interface
- `[cc1101.c:cc1101_init]`, `[cc1101.c:cc1101_init2]`, `[cc1101.c:cc1101_deinit]`, `[cc1101.c:cc1101_register]`, `[cc1101.c:cc1101_read]`, `[cc1101.c:cc1101_write]`, `[cc1101.c:cc1101_send]`, `[cc1101.c:cc1101_receive]`, `[cc1101.c:cc1101_setrf]`, `[cc1101.c:cc1101_setchannel]`, `[cc1101.c:cc1101_setpower]`, `[cc1101.c:cc1101_calc_rssi_dbm]`, `[cc1101.c:cc1101_dumpregs]` - TI CC1101 SPI transceiver initialization, character device registration (`/dev/cc1101`), and packet TX/RX APIs.
- `[ISM1_868MHzGFSK100kbps.c:cc1101_rfsettings_ISM1_868MHzGFSK100kbps]`, `[ISM2_433MHzMSK500kbps.c:cc1101_rfsettings_ISM2_433MHzMSK500kbps]`, `[ISM2_905MHzGFSK250kbps.c:cc1101_rfsettings_ISM2_905MHzGFSK250kbps]` - Precalculated CC1101 RF synthesizer and modem configuration structures.
- `[gs2200m.c:gs2200m_register]` - Registers the GainSpan GS2200M SPI Wi-Fi driver (`/dev/gs2200m` and `wlan0` network interface) supporting userspace socket offload (`USRSOCK`).
- `[nrf24l01.c:nrf24l01_register]`, `[nrf24l01.c:nrf24l01_init]`, `[nrf24l01.c:nrf24l01_send]`, `[nrf24l01.c:nrf24l01_sendto]`, `[nrf24l01.c:nrf24l01_recv]`, `[nrf24l01.c:nrf24l01_setpipeconfig]`, `[nrf24l01.c:nrf24l01_getpipeconfig]`, `[nrf24l01.c:nrf24l01_enablepipe]`, `[nrf24l01.c:nrf24l01_settxaddr]`, `[nrf24l01.c:nrf24l01_gettxaddr]`, `[nrf24l01.c:nrf24l01_setretransmit]`, `[nrf24l01.c:nrf24l01_settxpower]`, `[nrf24l01.c:nrf24l01_setdatarate]`, `[nrf24l01.c:nrf24l01_setradiofreq]`, `[nrf24l01.c:nrf24l01_changestate]` - Nordic nRF24L01 2.4 GHz SPI driver and `/dev/nrf24l01` character device interface.
- Subdirectories:
  - [./bluetooth/README.md](./bluetooth/README.md) - Bluetooth HCI drivers, H4/H5 UART transports, Classic/BLE bridge, and RPMSG HCI tunnel.
  - [./ieee80211/README.md](./ieee80211/README.md) - IEEE 802.11 Wi-Fi and IEEE 802.11ah Wi-Fi HaLow FullMAC drivers (`bcm43xxx`, `morse`).
  - [./ieee802154/README.md](./ieee802154/README.md) - IEEE 802.15.4 WPAN transceiver drivers (`at86rf23x`, `mrf24j40`, `xbee`).
  - [./lpwan/README.md](./lpwan/README.md) - LPWAN LoRa/FSK transceiver and LoRaWAN concentrator drivers (`rn2xx3`, `sx126x`, `sx127x`, `sx1301`).
  - [./spirit/README.md](./spirit/README.md) - STMicroelectronics SPIRIT1 sub-1 GHz RF library and 6LoWPAN network driver.

## Invariants
- `[cc1101.c:cc1101_open]`, `[gs2200m.c:gs2200m_open]`, and `[nrf24l01.c:nrf24l01_open]` assert `DEBUGASSERT(inode->i_private)`.
- `[gs2200m.c:gs2200m_register]` SPI transfer helpers assert `DEBUGASSERT(num <= 2032)`.

## Side Effects
- Registers `/dev/cc1101`, `/dev/gs2200m`, and `/dev/nrf24l01` character devices via `register_driver`, and registers `wlan0` via `netdev_register` in `gs2200m.c`.
- Locks SPI buses (`SPI_LOCK`), toggles chip-select and CE lines, attaches GPIO interrupt handlers, and schedules RX/TX packet processing on `HPWORK`/`LPWORK` (`work_queue`).

## Verification
- Run: `make test`
