# net_compat (`nuttx/arch/risc-v/src/gd32vw55x/gdwifi/net_compat`)

## Overview
Hardware abstraction and architecture package for `net_compat` under `nuttx/arch/risc-v/src/gd32vw55x/gdwifi/net_compat`, providing 2 header file(s) and 0 source file(s) (including `dhcpd.h`, `wifi_netif.h`).

## Subdirectories & Boundaries
- `lwip`: [./lwip/README.md](./lwip/README.md) - Hardware abstraction and architecture package for `lwip` under `nuttx/arch/risc-v/src/gd32vw55x/gdwifi/net_compat/lwip`, providing 6 header file(s) and 0 source file(s) (including `dhcp.h`, `ip_addr.h`, `lwip_napt.h`, `netif.h`).

## Interface
- `[dhcpd.h:dhcpd_delete_ipaddr_by_macaddr]`
- `[dhcpd.h:dhcpd_find_ipaddr_by_macaddr]`
- `[dhcpd.h:dhcpd_set_dns_server]`
- `[dhcpd.h:_GDWIFI_COMPAT_DHCPD_H]`
- `[dhcpd.h:PP_HTONL]`
- `[dhcpd.h:LWIP_MAKEU32]`
- `[wifi_netif.h:net_init]`
- `[wifi_netif.h:net_deinit]`
- `[wifi_netif.h:net_if_get_name]`
- `[wifi_netif.h:netif_is_up]`
- `[wifi_netif.h:net_if_add]`
- `[wifi_netif.h:net_if_remove]`
- `[wifi_netif.h:net_dhcpd_start]`
- `[wifi_netif.h:net_dhcpd_stop]`
- `[wifi_netif.h:net_if_up]`
- `[wifi_netif.h:net_if_down]`
- `[wifi_netif.h:net_if_find_from_name]`
- `[wifi_netif.h:net_if_is_static_ip]`
- `[wifi_netif.h:net_l2_send]`
- `[wifi_netif.h:net_if_set_ip]`
- `[wifi_netif.h:net_if_get_ip]`
- `[wifi_netif.h:net_if_set_default]`
- `[wifi_netif.h:net_dhcp_start]`
- `[wifi_netif.h:net_dhcp_stop]`
- `[wifi_netif.h:net_dhcp_release]`
- `[wifi_netif.h:net_dhcp_address_obtained]`
- `[wifi_netif.h:net_if_send_gratuitous_arp]`
- `[wifi_netif.h:net_ip_chksum]`
- `[wifi_netif.h:net_set_dns]`
- `[wifi_netif.h:net_get_dns]`
- [./lwip/README.md](./lwip/README.md)

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
