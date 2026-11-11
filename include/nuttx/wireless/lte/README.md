# NuttX LTE Wireless Subsystem (`include/nuttx/wireless/lte`)

## Overview
Defines the data structures, result/error codes, asynchronous event callbacks, and `SIOCLTECMD` socket/device `ioctl` commands for controlling LTE cellular modems (PDN session management, SIM/PIN, eDRX, PSM, cell quality, SMS, and firmware update).

## Interface
- `lte.h:lte_version`, `lte.h:lte_getpin`, `lte.h:lte_localtime`, `lte.h:lte_quality`, `lte.h:lte_cellinfo`, `lte.h:lte_edrx_setting`, `lte.h:lte_psm_setting`, `lte.h:lte_apn_setting`, `lte.h:lte_pdn_s`, `lte.h:lte_ipaddr_s` - LTE modem configuration, radio quality, power-saving mode, and PDN context structures.
- `lte.h:LTE_RESULT_OK`, `lte.h:LTE_RESULT_ERROR`, `lte.h:LTE_RESULT_CANCEL`, `lte.h:LTE_ENABLE`, `lte.h:LTE_DISABLE` - Standard LTE API return and state constants.
- `lte_ioctl.h:lte_ioctl_data_s`, `lte_ioctl.h:lte_evtctx_in_s`, `lte_ioctl.h:lte_evtctx_out_s`, `lte_ioctl.h:lte_smsreq_s` - Command and event-context multiplex structures passed through LTE `ioctl` calls.
- `lte_ioctl.h:SIOCLTECMD`, `lte_ioctl.h:SIOCSMSENSTREP`, `lte_ioctl.h:SIOCSMSGREFID`, `lte_ioctl.h:SIOCSMSSSCA`, `lte_ioctl.h:LTE_CMDID_POWERON`, `lte_ioctl.h:LTE_CMDID_ACTPDN` - Socket and character device `ioctl` command IDs for LTE and SMS control.

## Invariants
- In `lte_ioctl.h:lte_ioctl_data_s`, `inparam` and `outparam` pointer arrays must match `inparamlen` and `outparamlen` counts expected by the specific `cmdid` (`LTE_CMDID_*`).
- String fields in `lte.h:lte_apn_setting` (`apn`, `user_name`, `password`) must be NUL-terminated and not exceed `LTE_APN_LEN`, `LTE_APN_USERNAME_LEN`, and `LTE_APN_PASSWD_LEN`.

## Side Effects
- Issuing `lte_ioctl.h:SIOCLTECMD` dispatches synchronous or asynchronous commands to the underlying LTE modem daemon/driver, modifying radio attachment state, SIM PIN state, or PDN network interfaces.

## Verification
- Run: `make test`
