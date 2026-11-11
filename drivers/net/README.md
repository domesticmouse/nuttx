# Network Device Drivers (`drivers/net`)

## Overview
Provides the upper-half network device abstraction (`netdev_upperhalf`), virtual network interfaces (loopback, TUN/TAP, VLAN, Ethernet bridge, SLIP, Telnet, RPMSG netdev, Wi-Fi simulator), MDIO bus and PHY notification infrastructure, and hardware Ethernet/switch MAC drivers (Intel e1000/igb/igc PCIe NICs, ENC28J60, ENCX24J600, W5500, LAN91C111, LAN9250, DM90x0, FTMAC100, KSZ9477, and OA-TC6).

## Interface
- `[netdev_upperhalf.c:netdev_lower_register]`, `[netdev_upperhalf.c:netdev_lower_unregister]`, `[netdev_upperhalf.c:netdev_lower_carrier_on]`, `[netdev_upperhalf.c:netdev_lower_carrier_off]`, `[netdev_upperhalf.c:netdev_lower_rxready]`, `[netdev_upperhalf.c:netdev_lower_txdone]`, `[netdev_upperhalf.c:netpkt_alloc]`, `[netdev_upperhalf.c:netpkt_free]`, `[netdev_upperhalf.c:netpkt_copyin]`, `[netdev_upperhalf.c:netpkt_copyout]` - Upper-half network driver glue and IOB `netpkt` buffer management (`[netdev_upperhalf.c:struct netdev_upperhalf_s]`).
- `[netdev_drivers.c:netdev_drivers_init]`, `[loopback.c:localhost_initialize]`, `[tun.c:tun_initialize]`, `[vlan.c:vlan_register]`, `[vlan.c:vlan_unregister]`, `[bridge.c:bridge_ioctl]`, `[bridge.c:bridge_input]`, `[slip.c:slip_initialize]`, `[telnet.c:telnet_initialize]`, `[rpmsgdrv.c:net_rpmsg_drv_init]`, `[rpmsgdrv.c:net_rpmsg_drv_server_init]`, `[wifi_sim.c:wifi_sim_init]` - Virtual, tunnel, bridge, serial, remote-processor, and simulated wireless network interfaces.
- `[mdio.c:mdio_register]`, `[mdio.c:mdio_unregister]`, `[mdio.c:mdio_read]`, `[mdio.c:mdio_write]`, `[mdio.c:mdio_c45_read]`, `[mdio.c:mdio_c45_write]`, `[phy_notify.c:phy_notify_subscribe]`, `[phy_notify.c:phy_notify_unsubscribe]` - MDIO bus abstraction (`[mdio.c:struct mdio_bus_s]`) and PHY interrupt signal delivery.
- `[e1000.c:pci_e1000_init]`, `[igb.c:pci_igb_init]`, `[igc.c:pci_igc_init]`, `[dm90x0.c:dm9x_initialize]`, `[enc28j60.c:enc_initialize]`, `[encx24j600.c:enc_initialize]`, `[ftmac100.c:ftmac100_initialize]`, `[ksz9477.c:ksz9477_init]`, `[ksz9477_i2c.c:ksz9477_i2c_init]`, `[lan91c111.c:lan91c111_initialize]`, `[lan9250.c:lan9250_initialize]`, `[w5500.c:w5500_initialize]` - Hardware Ethernet NIC and switch drivers.
- Subdirectories:
  - [./oa_tc6/README.md](./oa_tc6/README.md) - OPEN Alliance TC6 10BASE-T1S SPI MAC-PHY protocol core and LAN865x/NCV7410 drivers.
  - [./phy/README.md](./phy/README.md) - Generic Ethernet PHY management library (`phylib`) and vendor PHY drivers.

## Invariants
- Upper-half TX/RX packet processing runs either on a dedicated `netdev-%s` kernel thread or work queue (`[netdev_upperhalf.c:struct netdev_thread_s]`) and obeys quota limits on IOB chains.
- MDIO bus access is serialized via `[mdio.c:mdio_lock]` (`nxmutex_lock`), and bridge FDB access is protected by `[bridge.c:nxmutex_lock]`.

## Side Effects
- Registers network interfaces (`netdev_register`), VFS character devices (`/dev/tun`, `/dev/telnet`), PCI drivers (`e1000`, `igb`, `igc`), and RPMSG endpoints (`[rpmsgdrv.c:rpmsg_create_ept]`).
- Performs SPI, I2C, MDIO, and memory-mapped PCI BAR DMA/MMIO transfers and schedules work queue items (`work_queue`).

## Verification
- Run: `make test`
