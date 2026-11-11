# wifi (`nuttx/arch/arm/src/common/ameba/wifi`)

## Overview
Hardware abstraction and architecture package for `wifi` under `nuttx/arch/arm/src/common/ameba/wifi`, providing 0 header file(s) and 2 source file(s) (including `ameba_wifi.c`, `ameba_wifi_depend.c`).

## Subdirectories & Boundaries
- `include`: [./include/README.md](./include/README.md) - Hardware abstraction and architecture package for `include` under `nuttx/arch/arm/src/common/ameba/wifi/include`, providing 2 header file(s) and 0 source file(s) (including `ameba_lwip_off.h`, `lwip_netconf.h`).

## Interface
- `[ameba_wifi.c:ameba_wifi_start]`
- `[ameba_wifi.c:ameba_wifi_scan_start]`
- `[ameba_wifi.c:ameba_wifi_scan_results]`
- `[ameba_wifi.c:ameba_wifi_connect]`
- `[ameba_wifi.c:ameba_wifi_disconnect]`
- `[ameba_wifi.c:ameba_wifi_start_ap]`
- `[ameba_wifi.c:ameba_wifi_stop_ap]`
- `[ameba_wifi_depend.c:pbuf_alloc]`
- `[ameba_wifi_depend.c:pbuf_free]`
- `[ameba_wifi_depend.c:netif_adapter_wifi_recv_whc]`
- `[ameba_wifi_depend.c:ameba_wifi_txframe]`
- `[ameba_wifi_depend.c:ameba_wifi_get_mac]`
- `[ameba_wifi_depend.c:lwip_netif_set_up]`
- `[ameba_wifi_depend.c:lwip_netif_set_down]`
- `[ameba_wifi_depend.c:lwip_netif_set_link_up]`
- `[ameba_wifi_depend.c:lwip_netif_set_link_down]`
- `[ameba_wifi_depend.c:wifi_set_autoreconnect]`
- `[ameba_wifi_depend.c:wifi_stop_autoreconnect]`
- `[ameba_wifi_depend.c:rtw_reconn_new_conn]`
- `[ameba_wifi_depend.c:wifi_fast_connect_enable]`
- `[ameba_wifi_depend.c:lwip_get_gw]`
- `[ameba_wifi_depend.c:lwip_get_mask]`
- `[ameba_wifi_depend.c:lwip_get_mac]`
- `[ameba_wifi_depend.c:lwip_get_ipv6_enabled]`
- `[ameba_wifi_depend.c:lwip_is_valid_ip]`
- `[ameba_wifi_depend.c:lwip_wlan_set_netif_info]`
- `[ameba_wifi_depend.c:dhcps_ip_in_table_check]`
- `[ameba_wifi_depend.c:at_printf_indicate]`
- `[ameba_wifi_depend.c:get_eap_phase]`
- `[ameba_wifi_depend.c:eap_eapol_start_hdl]`
- [./include/README.md](./include/README.md)

## Invariants
- None

## Side Effects
- None

## Verification
- Run: `make test`
