# Ethernet PHY Library (`drivers/net/phy`)

## Overview
Implements the generic Ethernet PHY management library (`phylib`), including PHY device lifecycle, Clause-22 and Clause-45 MDIO register access helpers, generic PHY drivers, link state polling/interrupt state machine, and vendor-specific PHY drivers.

## Interface
- `[phy_device.c:phy_driver_register]`, `[phy_device.c:phy_device_create]`, `[phy_device.c:phy_device_scan]`, `[phy_device.c:phy_connect]`, `[phy_device.c:phy_disconnect]`, `[phy_device.c:phy_device_free]` - PHY driver registration, MDIO bus scanning, and MAC-to-PHY binding lifecycle (`[phy.h:struct phy_driver_s]`).
- `[phy_core.c:phy_start]`, `[phy_core.c:phy_stop]`, `[phy_core.c:phy_interrupt]`, `[phy_core.c:phy_ioctl]` - PHY state machine control, interrupt notification, and MII/ethtool ioctl handling.
- `[phy_access.c:phy_read]`, `[phy_access.c:phy_write]`, `[phy_access.c:phy_modify]`, `[phy_access.c:phy_set_bits]`, `[phy_access.c:phy_clear_bits]`, `[phy_access.c:phy_read_mmd]`, `[phy_access.c:phy_write_mmd]`, `[phy_access.c:phy_modify_mmd]`, `[phy_access.c:phy_read_paged]`, `[phy_access.c:phy_write_paged]`, `[phy_access.c:phy_modify_paged]` - Clause-22, Clause-45 MMD (`[phy.h:CONFIG_MDIO_CLAUSE_45]`), and paged PHY register accessors.
- Subdirectories:
  - [./realtek/README.md](./realtek/README.md) - Realtek RTL8221B 2.5Gbps and RTL9000B 100BASE-T1 Automotive PHY drivers and firmware patch tables.

## Invariants
- To prevent AB-BA deadlocks between `netdev` lock (`d_lock`) and `phydev->lock`, carrier state notifications (`netdev_lower_carrier_on` / `netdev_lower_carrier_off`) must only be invoked after releasing `phydev->lock` (`[phy_core.c:phy_check_link]`).
- Registered PHY drivers and devices cannot exceed `[phy_device.c:CONFIG_NET_PHYLIB_MAX_DRIVERS]` and `[phy_device.c:CONFIG_NET_PHYLIB_MAX_PHYS]`.

## Side Effects
- Schedules periodic link-monitoring or interrupt work items on `LPWORK` (`[phy_core.c:work_queue]`), performs MDIO bus transfers, and updates lower-half network carrier status.

## Verification
- Run: `make test`
