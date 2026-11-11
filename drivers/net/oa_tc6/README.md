# OPEN Alliance TC6 10BASE-T1S MAC-PHY Drivers (`drivers/net/oa_tc6`)

## Overview
Implements the OPEN Alliance TC6 (OA-TC6) Serial Peripheral Interface protocol core and lower-half 10BASE-T1S Ethernet MAC-PHY drivers for the Microchip LAN865x and ON Semiconductor NCV7410 controllers.

## Interface
- `[oa_tc6.c:oa_tc6_initialize]`, `[oa_tc6.c:oa_tc6_common_init]`, `[oa_tc6.c:oa_tc6_register]` - Initializes and registers an OA-TC6 lower-half network device (`[oa_tc6.h:struct oa_tc6_driver_s]`, `[oa_tc6.h:struct oa_tc6_ops_s]`).
- `[oa_tc6.c:oa_tc6_read_reg]`, `[oa_tc6.c:oa_tc6_write_reg]`, `[oa_tc6.c:oa_tc6_set_clear_bits]`, `[oa_tc6.c:oa_tc6_store_mac_addr]`, `[oa_tc6.c:oa_tc6_bitrev8]` - Control register access, bit manipulation, and MAC address helpers over the OA-TC6 SPI control protocol.
- `[oa_tc6_lan865x.c:lan865x_initialize]` - Initializes the Microchip LAN8650/LAN8651 10BASE-T1S MAC-PHY driver (`[oa_tc6_lan865x.c:struct lan865x_driver_s]`).
- `[oa_tc6_ncv7410.c:ncv7410_initialize]` - Initializes the onsemi NCV7410 10BASE-T1S MAC-PHY driver (`[oa_tc6_ncv7410.c:struct ncv7410_driver_s]`).

## Invariants
- Requires `CONFIG_SCHED_LPWORK` (`[oa_tc6.c:OA_TC6_WORK]`) and `CONFIG_IOB_NBUFFERS >= OA_TC6_TX_QUOTA + OA_TC6_RX_QUOTA` (`[oa_tc6.c:OA_TC6_TX_QUOTA]`, `[oa_tc6.c:OA_TC6_RX_QUOTA]`).
- SPI control/data chunk exchanges and recovery state transitions are serialized via `[oa_tc6.c:nxmutex_lock]`.

## Side Effects
- Performs full-duplex SPI chunk and register transfers (`[oa_tc6.c:SPI_EXCHANGE]`), schedules interrupt/IO/recovery work on `LPWORK` (`[oa_tc6.c:work_queue]`), and registers the network interface via `netdev_lower_register`.

## Verification
- Run: `make test`
