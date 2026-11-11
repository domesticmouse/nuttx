# NuttX IEEE 802.15.4 MAC Subsystem (`ieee802154`)

## Overview
IEEE 802.15.4 MAC layer state machine (`mac802154.c` and primitive handlers `mac802154_*.c`), primitive pool allocator (`ieee802154_primitive.c`), `/dev/ieeeN` character driver (`mac802154_device.c`), 6LoWPAN network radio driver (`mac802154_netdev.c`), and IEEE 802.15.4 loopback test driver (`mac802154_loopback.c`).

## Interface
- `[ieee802154_primitive.c:ieee802154_primitive_poolinit]`
- `[ieee802154_primitive.c:ieee802154_primitive_allocate]`
- `[ieee802154_primitive.c:ieee802154_primitive_addref]`
- `[ieee802154_primitive.c:ieee802154_primitive_free]`
- `[mac802154.c:mac802154_create]`
- `[mac802154.c:mac802154_TXENABLE]`
- `[mac802154.c:mac802154_rxenable]`
- `[mac802154.c:mac802154_rxdisable]`
- `[mac802154.c:mac802154_setchannel]`
- `[mac802154.c:mac802154_setpanid]`
- `[mac802154.c:mac802154_setsaddr]`
- `[mac802154.c:mac802154_seteaddr]`
- `[mac802154.c:mac802154_setcoordsaddr]`
- `[mac802154.c:mac802154_setcoordeaddr]`
- `[mac802154.c:mac802154_setcoord]`
- `[mac802154.c:mac802154_setdevmode]`
- `[mac802154.c:mac802154_txdesc_alloc]`
- `[mac802154.c:mac802154_setupdelegate]`
- `[mac802154.c:mac802154_notify]`
- `[mac802154_assoc.c:mac802154_req_associate]`
- `[mac802154_assoc.c:mac802154_resp_associate]`
- `[mac802154_assoc.c:mac802154_txdone_assocreq]`
- `[mac802154_assoc.c:mac802154_rx_assocreq]`
- `[mac802154_assoc.c:mac802154_rx_assocresp]`
- `[mac802154_assoc.c:mac802154_txdone_assocresp]`
- `[mac802154_assoc.c:mac802154_txdone_datareq_assoc]`
- `[mac802154_assoc.c:mac802154_timeout_assoc]`
- `[mac802154_disassoc.c:mac802154_req_disassociate]`
- `[mac802154_bind.c:mac802154_bind]`
- `[mac802154_data.c:mac802154_req_data]`
- `[mac802154_data.c:mac802154_txdone_data]`
- `[mac802154_get_mhrlen.c:mac802154_get_mhrlen]`
- `[mac802154_getset.c:mac802154_req_get]`
- `[mac802154_getset.c:mac802154_req_set]`
- `[mac802154_gts.c:mac802154_req_gts]`
- `[mac802154_ioctl.c:mac802154_ioctl]`
- `[mac802154_orphan.c:mac802154_resp_orphan]`
- `[mac802154_poll.c:mac802154_req_poll]`
- `[mac802154_poll.c:mac802154_txdone_datareq_poll]`
- `[mac802154_poll.c:mac802154_Polltimeout]`
- `[mac802154_purge.c:mac802154_req_purge]`
- `[mac802154_reset.c:mac802154_req_reset]`
- `[mac802154_rxenable.c:mac802154_req_rxenable]`
- `[mac802154_scan.c:mac802154_req_scan]`
- `[mac802154_scan.c:mac802154_txdone_beaconreq]`
- `[mac802154_scan.c:mac802154_edscan_Wait]`
- `[mac802154_start.c:mac802154_req_start]`
- `[mac802154_sync.c:mac802154_req_sync]`
- `[mac802154_device.c:mac802154dev_register]`
- `[mac802154_netdev.c:mac802154netdev_register]`
- `[mac802154_loopback.c:ieee8021514_loopback]`

## Invariants
- `[ieee802154_primitive.c:ieee802154_primitive_poolinit]` initializes the primitive pools (`g_primfree` and `g_primfree_irq`) at most once (`g_poolinit`).
- `[ieee802154_primitive.c:ieee802154_primitive_allocate]` never calls `kmm_zalloc` from interrupt context (`up_interrupt_context()`), and `[ieee802154_primitive.c:ieee802154_primitive_free]` asserts `prim->nclients == 0` and frees via `kmm_free` only when `prim->pool == IEEE802154_POOL_DYNAMIC`.
- `[mac802154.c:mac802154_tryop]` permits only one exclusive MAC operation (`priv->cmd != MAC802154_CMD_NONE`) unless `wait == true`, in which case the caller blocks on `priv->opsem`.
- `[mac802154_bind.c:mac802154_bind]` keeps the MAC receiver callback list `priv->cb_list` sorted in descending order of `cb->prio`.
- `[mac802154_device.c:mac802154dev_open]` permits only one open file instance at a time (`dev->md_open != NULL` returns `-EBUSY`); `[mac802154_device.c:mac802154dev_notify]` drops incoming data frames when `dev->ndataind >= CONFIG_IEEE802154_MACDEV_RXQUEUE` (returning `-ENOBUFS`).
- `[mac802154_loopback.c:lo_req_data]` asserts `iob->io_offset == MAC_HDRLEN` (9 bytes).

## Side Effects
- `[mac802154.c:mac802154_create]` initializes the primitive pool via `ieee802154_primitive_poolinit`, allocates `struct ieee802154_privmac_s` and the transaction descriptor pool via `kmm_zalloc`, binds radio callbacks via `radio->bind`, and resets the MAC PIB attributes.
- `[mac802154.c]` schedules RX, TX-done, purge, and timer work items on `HPWORK`/`LPWORK`, controls the lower-half radio driver (`rxenable`, `txdelayed`, `set_attr`, `beaconstart`/`beaconupdate`), and dispatches primitives to bound callbacks via `mac802154_notify`.
- `[mac802154_device.c:mac802154dev_register]` allocates `struct mac802154_chardevice_s`, binds `mac802154dev_notify` to the MAC layer, and registers `/dev/ieeeN` via `register_driver`; `[mac802154_device.c:mac802154dev_notify]` queues primitives/frames, wakes blocked readers/ioctl waiters via `nxsem_post`, and sends notifications via `nxsig_notification`.
- `[mac802154_netdev.c:mac802154netdev_register]` allocates `struct macnet_driver_s`, binds `macnet_notify` to the MAC layer, registers the `NET_LL_IEEE802154` network device via `netdev_register`, and feeds incoming data indications into `sixlowpan_input` under `net_lock()`.
- `[mac802154_loopback.c:ieee8021514_loopback]` initializes `g_loopback`, registers the `NET_LL_IEEE802154` loopback device via `netdev_register`, brings the interface up, and loops queued frames back into `sixlowpan_input` via `lo_loopback_work` on `LPWORK`.

## Verification
- Run: `make test`
