# NuttX IEEE 802.11 (Wi-Fi) Subsystem (`include/nuttx/wireless/ieee80211`)

## Overview
Defines IEEE 802.11 MAC frame headers, information element (`IE`) constants, sequence number helpers, cryptographic cipher/AKM structures (`ieee80211.h`, `ieee80211_cypto.h`), and Broadcom FullMAC (`bcmf`) Wi-Fi driver interfaces over SDIO and gSPI buses (`bcmf_board.h`, `bcmf_sdio.h`, `bcmf_gspi.h`, `bcmf_netdev.h`, `bcmf_gpio.h`).

## Interface
- `ieee80211.h:ieee80211_hdr`, `ieee80211.h:ieee80211_hdr_3addr`, `ieee80211.h:ieee80211_qos_hdr`, `ieee80211.h:ieee80211s_hdr`, `ieee80211.h:ieee80211_is_mgmt`, `ieee80211.h:ieee80211_is_ctl`, `ieee80211.h:ieee80211_is_data`, `ieee80211.h:ieee80211_sn_less`, `ieee80211.h:ieee80211_sn_inc` - 802.11 MAC frame structures, frame control (`IEEE80211_FCTL_*`) predicates, and modulo-4096 sequence number arithmetic.
- `ieee80211_cypto.h:ieee80211_cipher`, `ieee80211_cypto.h:ieee80211_akm`, `ieee80211_cypto.h:ieee80211_key`, `ieee80211_cypto.h:ieee80211_pmk` - WEP/TKIP/CCMP/BIP cipher enumerations, AKM suites, and key/PMK material descriptors.
- `bcmf_board.h:bcmf_board_initialize`, `bcmf_board.h:bcmf_board_power`, `bcmf_board.h:bcmf_board_reset`, `bcmf_board.h:bcmf_board_setup_oob_irq`, `bcmf_board.h:bcmf_board_etheraddr` - Board-level power, reset, out-of-band interrupt, and MAC address hooks required by Broadcom FullMAC drivers.
- `bcmf_sdio.h:bcmf_sdio_initialize`, `bcmf_gspi.h:gspi_dev_s`, `bcmf_gspi.h:bcmf_gspi_initialize`, `bcmf_netdev.h:bcmf_netdev_register`, `bcmf_gpio.h:bcmf_set_gpio`, `bcmf_gpio.h:bcmf_get_gpio` - Broadcom FullMAC SDIO/gSPI bus initialization, network device registration, and chip GPIO accessors.

## Invariants
- 802.11 frame header structures in `ieee80211.h` (`struct ieee80211_hdr`, `struct ieee80211_qos_hdr`) use `aligned_data(2)` and little-endian `frame_control` / `seq_ctrl` fields per the IEEE 802.11 wire format.
- `bcmf_board.h:bcmf_board_initialize` must be called to configure power/reset/OOB-IRQ GPIOs before initializing the SDIO or gSPI bus driver via `bcmf_sdio.h:bcmf_sdio_initialize` or `bcmf_gspi.h:bcmf_gspi_initialize`.

## Side Effects
- `bcmf_sdio.h:bcmf_sdio_initialize` and `bcmf_gspi.h:bcmf_gspi_initialize` power-cycle the WLAN chip, download firmware and NVRAM images over SDIO/gSPI, spawn a control thread, and register a `wlan*` network interface via `bcmf_netdev.h:bcmf_netdev_register`.

## Verification
- Run: `make test`
