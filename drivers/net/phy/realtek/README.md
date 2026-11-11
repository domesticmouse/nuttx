# Realtek Ethernet PHY Drivers (`drivers/net/phy/realtek`)

## Overview
Provides Ethernet PHY drivers and Clause-45 MMD firmware patch tables (`ramcode`) for the Realtek RTL8221B 2.5Gbps PHY and RTL9000B 100BASE-T1 Automotive Ethernet PHY.

## Interface
- `[rtl8221b.c:rtl8221b_register]` - Registers the Realtek RTL8221B 2.5Gbps PHY driver (`[rtl8221b.c:g_rtl8221b_driver]`, `[rtl8221b_fw.h:struct rtl8221b_mmd_reg_s]`).
- `[rtl9000b.c:rtl9000b_register]` - Registers the Realtek RTL9000B 100BASE-T1 Automotive PHY driver (`[rtl9000b.c:g_rtl9000b_driver]`).

## Invariants
- Firmware patch sequences (`rtl8221b_apply_patch`, `rtl9000b_init_config`) require Clause-45 MMD access (`phy_read_mmd`, `phy_write_mmd`) and must complete before link auto-negotiation is started.

## Side Effects
- Registers `struct phy_driver_s` entries with the PHY subsystem via `phy_driver_register` and writes vendor MMD registers and firmware ramcode over the MDIO bus.

## Verification
- Run: `make test`
