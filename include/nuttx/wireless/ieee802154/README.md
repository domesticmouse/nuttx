# NuttX IEEE 802.15.4 Wireless Subsystem (`include/nuttx/wireless/ieee802154`)

## Overview
Provides the IEEE 802.15.4 Medium Access Control (`MAC`) layer (`ieee802154_mac.h`), lower-half radio transceiver abstraction (`ieee802154_radio.h`), character device frame wrappers (`ieee802154_device.h`), loopback driver (`ieee802154_loopback.h`), and hardware transceiver driver interfaces (Microchip MRF24J40, Atmel AT86RF23x, and Digi XBee).

## Interface
- `ieee802154_mac.h:MACHANDLE`, `ieee802154_mac.h:ieee802154_status_e`, `ieee802154_mac.h:ieee802154_attr_e`, `ieee802154_mac.h:ieee802154_frametype_e`, `ieee802154_mac.h:ieee802154_addr_s`, `ieee802154_mac.h:ieee802154_primitive_s`, `ieee802154_mac.h:mac802154_create`, `ieee802154_mac.h:mac802154dev_register`, `ieee802154_mac.h:mac802154netdev_register`, `ieee802154_mac.h:ieee802154_primitivepool_initialize`, `ieee802154_mac.h:ieee802154_primitive_allocate`, `ieee802154_mac.h:ieee802154_primitive_free` - IEEE 802.15.4 MAC instance creation, character/6LoWPAN network device bindings, PIB attributes, and reference-counted MAC primitive pool.
- `ieee802154_radio.h:ieee802154_radio_s`, `ieee802154_radio.h:ieee802154_radiocb_s`, `ieee802154_radio.h:ieee802154_txdesc_s`, `ieee802154_radio.h:ieee802154_beaconframe_s` - Lower-half radio operations vtable (`bind`, `reset`, `getattr`, `setattr`, `txnotify`, `txdelayed`, `rxenable`, `energydetect`, `beaconstart`, `beaconupdate`, `beaconstop`, `sfupdate`) and MAC event callbacks.
- `ieee802154_device.h:mac802154dev_txframe_s`, `ieee802154_device.h:mac802154dev_rxframe_s`, `ieee802154_device.h:MAC802154IOC_MLME_ASSOC_REQUEST` - Character driver frame structures and MLME/MCPS `ioctl` commands.
- `ieee802154_loopback.h:ieee8021514_loopback`, `at86rf23x.h:at86rf23x_lower_s`, `at86rf23x.h:at86rf23x_init`, `mrf24j40.h:mrf24j40_lower_s`, `mrf24j40.h:mrf24j40_init`, `xbee.h:XBEEHANDLE`, `xbee.h:xbee_lower_s`, `xbee.h:xbee_init`, `xbee.h:xbee_netdev_register` - Loopback and hardware transceiver drivers.

## Invariants
- Primitives allocated via `ieee802154_mac.h:ieee802154_primitive_allocate` are reference-counted (`nclients`) and must be released by every consumer via `ieee802154_mac.h:ieee802154_primitive_free` after notification delivery.
- `ieee802154_mac.h:ieee802154_primitivepool_initialize` must be invoked before creating or binding any MAC or radio driver instance.

## Side Effects
- `ieee802154_mac.h:mac802154dev_register` and `ieee802154_mac.h:mac802154netdev_register` register `/dev/ieee*` character devices or `wpan*` 6LoWPAN network interfaces.
- Radio drivers (`at86rf23x.h:at86rf23x_init`, `mrf24j40.h:mrf24j40_init`, `xbee.h:xbee_init`) attach GPIO interrupt handlers and perform SPI transactions to configure RF channels, PAN IDs, and hardware frame filters.

## Verification
- Run: `make test`
