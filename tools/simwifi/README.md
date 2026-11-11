# simwifi

## Overview
Host-side Wi-Fi simulation environment manager (`tools/simwifi`) for the NuttX Simulator (`sim`). Supports both `mac80211_hwsim` virtual radios (`HWSIM` mode, pairing virtual STA `wlan0` and AP `wlan1`) and real wireless network cards (`RNC` mode) bridged to `nuttx0`.

## Interface
- `sim_wifi.sh:init`, `sim_wifi.sh:clean` - Initializes or tears down `/var/run/simwifi`, configures `nuttx0` bridge routing via `simhostroute.sh`, loads/unloads `mac80211_hwsim`, and toggles NetworkManager/rfkill Wi-Fi state.
- `sim_wifi.sh:start_hwsim`, `sim_wifi.sh:stop_hwsim`, `sim_wifi.sh:start_sta`, `sim_wifi.sh:stop_sta`, `sim_wifi.sh:start_ap`, `sim_wifi.sh:stop_ap`, `sim_wifi.sh:start_staap`, `sim_wifi.sh:stop_staap`, `sim_wifi.sh:start_net`, `sim_wifi.sh:stop_net` - State-machine commands (`SW_INIT`, `SW_HWSIM`, `SW_STA`, `SW_AP`, `SW_STAAP`, `SW_NET`) managing `wpa_supplicant`, `hostapd`, `dnsmasq`, and `udhcpc`.
- `sim_wifi.sh:rename_ifdev`, `sim_wifi.sh:show_status` - Renames host wireless interfaces to `wlanX` and dumps active daemon processes, bridge links, routes, and `/var/run/simwifi/simwifi.state`.
- `udhcpc.script:log` - BusyBox `udhcpc` dispatcher script (`bound`, `renew`, `deconfig`, `leasefail`, `nak`) that configures IP/netmask, default routes, and `/etc/resolv.conf`.

## Invariants
- Requires root privileges (`sudo`) and host binaries `udhcpc`, `dnsmasq`, `wpa_supplicant`, `hostapd`, `nmcli`, `rfkill`, `ip`, and `ifconfig`.
- State transitions in `sim_wifi.sh:set_state` are restricted to `SW_INIT`, `SW_HWSIM`, `SW_NET`, `SW_STA`, `SW_AP`, and `SW_STAAP`, persisted in `/var/run/simwifi/simwifi.state`.

## Side Effects
- Creates and modifies `/var/run/simwifi/*`, `/var/udhcpc.script`, `/usr/bin/sim_wifi.sh` symlink, and `/etc/resolv.conf`.
- Loads/unloads the `mac80211_hwsim` kernel module (`modprobe`), mutates host network interfaces/bridges/routes (`nuttx0`, `wlan0`, `wlan1`), disables/enables NetworkManager Wi-Fi (`nmcli radio wifi`), and spawns/kills `wpa_supplicant`, `hostapd`, `dnsmasq`, and `udhcpc`.

## Verification
- Run: `make test`
