# NuttX Wireless Subsystem (`wireless`)

## Overview
Top-level wireless subsystem build and configuration aggregator (`Makefile`, `CMakeLists.txt`, `Kconfig`) that groups Bluetooth Low Energy (`bluetooth`), IEEE 802.15.4 MAC (`ieee802154`), and generic packet radio (`pktradio`) subsystems into `libwireless`.

## Subdirectories & Boundaries
- [`bluetooth`](./bluetooth/README.md) - Bluetooth Low Energy (BLE) host stack, HCI core, L2CAP, ATT, GATT, SMP, and network device interface.
- [`ieee802154`](./ieee802154/README.md) - IEEE 802.15.4 MAC layer state machine, primitive allocator, character driver, and 6LoWPAN network driver.
- [`pktradio`](./pktradio/README.md) - Non-IEEE 802.15.4 packet radio metadata allocator and network loopback driver.
