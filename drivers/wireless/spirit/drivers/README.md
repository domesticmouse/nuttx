# STMicroelectronics SPIRIT1 Network Device Driver (`drivers/wireless/spirit/drivers`)

## Overview
Implements the NuttX IEEE 802.15.4 / 6LoWPAN network device driver (`spirit_netdev.c`) for STMicroelectronics SPIRIT1 sub-1 GHz low-power RF transceivers using the SPIRIT1 library.

## Interface
- `[spirit_netdev.c:spirit_netdev_initialize]` - Allocates a SPIRIT1 driver instance (`struct spirit_driver_s`), initializes the radio hardware (`spirit_hw_initialize`), attaches the GPIO interrupt handler, and registers a 6LoWPAN network device (`wpanN`) via `netdev_register`.

## Invariants
- `[spirit_netdev.c:spirit_netdev_initialize]` and internal workers assert `DEBUGASSERT(priv != NULL)`, `DEBUGASSERT(priv->lower != NULL && priv->lower->enable != NULL)`, and `DEBUGASSERT(pktmeta != NULL)`.

## Side Effects
- Toggles the SPIRIT1 SDN (shutdown) pin via `priv->lower->reset`/`enable`, performs SPI transactions to configure STack packet format, CSMA, and whitening, schedules RX/TX/poll work on `HPWORK` and `LPWORK`, and registers a network interface via `netdev_register`.

## Verification
- Run: `make test`
