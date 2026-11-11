# NuttX Cellular Network Interface (`include/nuttx/wireless/cellular`)

## Overview
Defines network `ioctl` commands and request structures (`struct icellreq`, `struct cellnetinfo_s`) for configuring and querying cellular network interfaces (`cell*`) in NuttX.

## Interface
- `cellular.h:cellnetinfo_s`, `cellular.h:icellreq` - Cellular network interface parameter structure (`mdp_chnidx`) and `ioctl` request wrapper (`ifr_name`, `ifr_cellinfo`, `ifr_celldata`).
- `cellular.h:SIOCSCELLNETDEV`, `cellular.h:SIOCGCELLNETDEV`, `cellular.h:IFCELLDEVPARAMSIZ` - Socket `ioctl` commands for setting and retrieving cellular network device parameters.

## Invariants
- The interface name `ifr_name` in `cellular.h:icellreq` must be NUL-terminated and fit within `IFNAMSIZ` bytes.

## Side Effects
- Issuing `cellular.h:SIOCSCELLNETDEV` mutates the cellular driver's channel binding or hardware configuration for the target network interface.

## Verification
- Run: `make test`
