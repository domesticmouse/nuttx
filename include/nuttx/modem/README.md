# Modem Driver Interfaces (`include/nuttx/modem`)

## Overview
Defines character driver interfaces, ioctl commands, and lower-half operations for cellular modems in NuttX, including Sony/Altair ALT1250 LTE-M modem protocol containers and event buffers (`alt1250.h`), generic modem power/reset ioctl commands (`ioctl.h`), and u-blox modem control interfaces (`u-blox.h`).

## Interface
- `ioctl.h:MODEM_IOC_POWERON`, `ioctl.h:MODEM_IOC_POWEROFF`, `ioctl.h:MODEM_IOC_RESET`, `ioctl.h:MODEM_IOC_GETSTATUS`
- `alt1250.h:alt1250_register`, `alt1250.h:compose_handler_t`, `alt1250.h:parse_handler_t`, `alt1250.h:ALT1250_IOC_POWER`, `alt1250.h:ALT1250_IOC_SEND`, `alt1250.h:ALT1250_IOC_SETEVTBUFF`, `alt1250.h:ALT1250_IOC_EXCHGCONTAINER`, `alt1250.h:ALT1250_EVTBIT_RESET`, `alt1250.h:ALT1250_EVTBIT_REPLY`, `alt1250.h:ALTCOM_FD_SET`, `alt1250.h:ALTCOM_FD_CLR`, `alt1250.h:ALTCOM_FD_ISSET`, `alt1250.h:ALTCOM_FD_ZERO`
- `u-blox.h:struct ubxmdm_regval`, `u-blox.h:struct ubxmdm_status`, `u-blox.h:struct ubxmdm_ops`, `u-blox.h:struct ubxmdm_lower`, `u-blox.h:ubxmdm_register`, `u-blox.h:ubxmdm_unregister`

## Invariants
- Socket descriptors passed to `alt1250.h:ALTCOM_FD_SET`, `alt1250.h:ALTCOM_FD_CLR`, and `alt1250.h:ALTCOM_FD_ISSET` are bounds-checked to `0 <= s < ALTCOM_FD_SETSIZE` (`ALTCOM_NSOCKET`).

## Side Effects
- `alt1250.h:alt1250_register` and `u-blox.h:ubxmdm_register` register modem character device nodes in the VFS namespace.
- Modem ioctl commands (`ioctl.h:MODEM_IOC_POWERON`, `alt1250.h:ALT1250_IOC_SEND`) perform SPI or GPIO hardware operations to power, reset, or exchange command packets with cellular baseband hardware.

## Verification
- Run: `make test`
