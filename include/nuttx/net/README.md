# Network Stack & Driver Interfaces (`include/nuttx/net`)

## Overview
Defines the core network protocol headers, socket internal interfaces, network device upper/lower-half abstractions, PHY/MDIO bus management, and NIC driver interfaces for NuttX. Covers IPv4, IPv6, TCP, UDP, ICMP/ICMPv6, IGMP, MLD, DNS, ARP/Neighbor Discovery, 6LoWPAN, IEEE 802.15.4, Bluetooth L2CAP/H4, SocketCAN/CAN gateway, Ethernet/VLAN/Bridging, Netlink, RPMSG networking, USRSOCK, packet snooping, and NIC/PHY drivers (`e1000`, `igb`, `igc`, `dm90x0`, `enc28j60`, `encx24j600`, `ftmac100`, `ksz9477`, `lan91c111`, `lan9250`, `oa_tc6`, `w5500`, `wifi_sim`), plus the Netfilter subpackage (`./netfilter/README.md`).

## Interface
- `./netfilter/README.md` - Netfilter hooks, Xtables match/target descriptors, IPv4/IPv6 rule tables, and NAT structures
- `net.h:struct sock_intf_s`, `net.h:struct socket_conn_s`, `net.h:enum net_lltype_e`, `net.h:psock_getsockopt`, `net.h:psock_setsockopt`, `net.h:psock_getsockname`, `net.h:psock_getpeername`, `net.h:psock_ioctl`, `net.h:psock_shutdown`, `net.h:psock_poll`, `net.h:netdev_register`, `net.h:netdev_unregister`, `net.h:netdev_lock`, `net.h:netdev_unlock`, `net.h:netdev_findbyname`, `net.h:netdev_findbyindex`
- `netdev.h:struct net_driver_s`, `netdev.h:netdev_iob_clear`, `netdev.h:netdev_iob_release`, `netdev.h:netdev_iob_clone`, `netdev.h:netdev_ipv6_add`, `netdev.h:netdev_ipv6_del`, `netdev.h:netdev_ipv6_lookup`, `netdev.h:netdev_ipv6_foreach`
- `netdev_lowerhalf.h:struct netdev_lowerhalf_s`, `netdev_lowerhalf.h:struct netdev_ops_s`, `netdev_lowerhalf.h:struct wireless_ops_s`, `netdev_lowerhalf.h:netpkt_t`, `netdev_lowerhalf.h:netdev_lower_register`, `netdev_lowerhalf.h:netdev_lower_unregister`, `netdev_lowerhalf.h:netdev_lower_carrier_on`, `netdev_lowerhalf.h:netdev_lower_carrier_off`, `netdev_lowerhalf.h:netdev_lower_rxready`, `netdev_lowerhalf.h:netdev_lower_txdone`, `netdev_lowerhalf.h:netpkt_alloc`, `netdev_lowerhalf.h:netpkt_free`, `netdev_lowerhalf.h:netpkt_copyin`, `netdev_lowerhalf.h:netpkt_copyout`
- `ip.h:struct ipv4_hdr_s`, `net_ipv6addr_t`, `ip.h:struct ipv6_hdr_s`, `ip.h:union ip_addr_u`, `ip.h:net_ipv6addr_maskcmp`, `ipopt.h:IPOPT_MKTYPE`, `ipv6ext.h:struct ipv6_extension_s`, `ipv6ext.h:ipv6_exthdr`
- `tcp.h:struct tcp_hdr_s`, `tcp.h:struct tcp_stats_s`, `udp.h:struct udp_hdr_s`, `udp.h:struct udp_stats_s`, `icmp.h:struct icmp_hdr_s`, `icmpv6.h:struct icmpv6_hdr_s`, `igmp.h:struct igmp_hdr_s`, `mld.h:struct mld_mcast_listen_query_s`, `neighbor.h:struct neighbor_entry_s`
- `ethernet.h:struct eth_hdr_s`, `ethernet.h:struct eth_8021qhdr_s`, `vlan.h:vlan_register`, `vlan.h:vlan_unregister`, `bridge.h:bridge_ioctl`, `bridge.h:bridge_input`, `if_bridge.h:BRCTL_ADD_BRIDGE`
- `dns.h:struct dns_header_s`, `dns.h:dns_add_nameserver`, `dns.h:dns_foreach_nameserver`, `dns.h:dns_register_notify`
- `mdio.h:struct mdio_bus_s`, `mdio.h:struct mdio_ops_s`, `mdio.h:mdio_register`, `mdio.h:mdio_read`, `mdio.h:mdio_write`, `mii.h:struct phy_desc_s`, `gmii.h:GMII_MCR`, `phy.h:struct phy_device_s`, `phy.h:phy_device_create`, `phy.h:phy_connect`, `phy.h:phy_start`, `realtek_phy.h:rtl8221b_register`
- `can.h:can_input`, `cangw.h:struct cangw_rule_s`, `bluetooth.h:bluetooth_input`, `ieee802154.h:ieee802154_input`, `radiodev.h:struct radio_driver_s`, `sixlowpan.h:sixlowpan_input`, `rfc6775.h:struct sixlowpan_6co_s`
- `netlink.h:netlink_add_response`, `netlink.h:netlink_add_broadcast`, `netpoll.h:struct netpoll_s`, `netpoll.h:netpoll_udp_init`, `netpoll.h:netpoll_udp_send`, `netstats.h:struct net_stats_s`, `netstats.h:g_netstats`, `snoop.h:struct snoop_s`, `snoop.h:snoop_open`, `snoop.h:snoop_dump`
- `loopback.h:localhost_initialize`, `slip.h:slip_initialize`, `tun.h:tun_initialize`, `telnet.h:telnet_initialize`, `pkt.h:pkt_input`, `rpmsg.h:struct net_rpmsg_header_s`, `rpmsgdrv.h:net_rpmsg_drv_init`, `sms.h:struct sms_send_msg_s`, `usrsock.h:usrsock_register`, `usrsock.h:usrsock_request`, `usrsock.h:usrsock_response`
- `dm90x0.h:dm9x_initialize`, `e1000.h:pci_e1000_init`, `enc28j60.h:enc_initialize`, `encx24j600.h:enc_initialize`, `ftmac100.h:ftmac100_initialize`, `igb.h:pci_igb_init`, `igc.h:pci_igc_init`, `ksz9477.h:ksz9477_i2c_init`, `lan91c111.h:lan91c111_initialize`, `lan9250.h:lan9250_initialize`, `oa_tc6.h:oa_tc6_initialize`, `w5500.h:w5500_initialize`, `wifi_sim.h:wifi_sim_init`

## Invariants
- Socket descriptors (`net.h:struct socket`) must satisfy `net.h:_PS_VALID` (`_PS_ALLOCD(psock) && _PS_INITD(psock)`) before invoking socket interface callbacks in `net.h:struct sock_intf_s`.
- Lower-half network drivers (`netdev_lowerhalf.h:struct netdev_lowerhalf_s`) track TX and RX packet buffer allocations against per-queue atomic quotas (`quota[NETPKT_TYPENUM]`).
- Access to network device state (`netdev.h:struct net_driver_s`), MDIO buses (`mdio.h:struct mdio_bus_s`), PHY state machines (`phy.h:struct phy_device_s`), and USRSOCK state (`usrsock.h:usrsock_lock`) must be serialized using their respective locks (`net.h:netdev_lock`, `mdio.h:mdio_lock`, `phydev->lock`, `g_usrsock_lock`).

## Side Effects
- Network device registration (`net.h:netdev_register`, `netdev_lowerhalf.h:netdev_lower_register`, `vlan.h:vlan_register`) mutates the global network interface registry and binds link-layer framing and MTU settings.
- Packet input/transmit routines (`netdev_lowerhalf.h:netdev_lower_rxready`, `can.h:can_input`, `sixlowpan.h:sixlowpan_input`, `netpoll.h:netpoll_udp_send`) allocate/free IOB chains (`netpkt_t`), schedule worker threads (`LPWORK`), update `netstats.h:g_netstats` counters, and perform DMA/MMIO/SPI/MDIO hardware transfers.
- `snoop.h:snoop_open` and `snoop.h:snoop_dump` write packet capture records to a VFS file (`struct file`).

## Verification
- Run: `make test`
