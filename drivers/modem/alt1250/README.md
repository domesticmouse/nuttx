# Sony Altair ALT1250 LTE Modem Driver (`drivers/modem/alt1250`)

## Overview
Implements the character driver, SPI packet transport, power/wakelock state machine, and ALTCOM v1/v4 command composition and response parsing handlers for the Sony Altair ALT1250 cellular LTE-M/NB-IoT modem.

## Interface
- `[alt1250.c:alt1250_register]`, `[alt1250.h:get_event_lapibuffer]` - Registers the `/dev/alt1250` character device and manages event buffers for LAPI notifications.
- `[altmdm.h:altmdm_init]`, `[altmdm.h:altmdm_fin]`, `[altmdm.h:altmdm_read]`, `[altmdm.h:altmdm_write]`, `[altmdm.h:altmdm_poweron]`, `[altmdm.h:altmdm_poweroff]`, `[altmdm.h:altmdm_reset]`, `[altmdm.h:altmdm_take_wlock]`, `[altmdm.h:altmdm_give_wlock]`, `[altmdm.h:altmdm_count_wlock]`, `[altmdm.h:altmdm_get_reset_reason]` - Core modem state machine, SPI transport orchestration, and wakelock control (`[altmdm.c:struct altmdm_dev_s]`).
- `[altmdm_spi.h:altmdm_spipkt_init]`, `[altmdm_spi.h:altmdm_do_hdr_transaction]`, `[altmdm_spi.h:altmdm_do_body_transaction]` - Low-level SPI header/body packet transactions (`[altmdm_spi.h:struct altmdm_spipkt_s]`).
- `[altmdm_event.h:altmdm_event_init]`, `[altmdm_event.h:altmdm_event_wait]`, `[altmdm_event.h:altmdm_event_set]`, `[altmdm_event.h:altmdm_event_clear]` - Thread event synchronization primitives (`[altmdm_event.h:struct altmdm_event_s]`).
- `[altcom_pkt.h:altcom_make_header]`, `[altcom_pkt.h:altcom_is_pkt_ok]`, `[altcom_errno.h:altcom_errno2nuttx]` - ALTCOM protocol framing, checksum validation, and error translation.
- `[altcom_hdlr_socket.h:altcom_socket_pkt_compose]`, `[altcom_hdlr_net.h:altcom_getnetinfo_pkt_compose]`, `[altcom_hdlr_pdn.h:altcom_actpdn_pkt_compose]`, `[altcom_hdlr_sms.h:altcom_smssend_pkt_compose]`, `[altcom_hdlr_sim.h:altcom_getsiminfo_pkt_compose]`, `[altcom_hdlr_pin.h:altcom_enterpin_pkt_compose]`, `[altcom_hdlr_psave.h:altcom_setpsm_pkt_compose]`, `[altcom_hdlr_radio.h:altcom_radioon_pkt_compose]`, `[altcom_hdlr_firmware.h:altcom_execupdate_pkt_compose]`, `[altcom_hdlr_log.h:altcom_logread_pkt_compose]`, `[altcom_hdlr_other.h:altcom_sendatcmd_pkt_compose]` - ALTCOM subsystem packet composers and parsers.

## Invariants
- Only a single `/dev/alt1250` instance (`[alt1250.c:g_alt1250_dev]`) may be active; event buffer access is synchronized with mutexes (`[alt1250.c:nxmutex_lock]`) and critical sections (`[altmdm_event.c:enter_critical_section]`).
- SPI packet headers and checksums must pass `[altcom_pkt.c:altcom_is_pkt_ok]` and `[altmdm_spi.c:altmdm_is_valid_spipkt_header]` before payload parsing.

## Side Effects
- Registers the `/dev/alt1250` character driver (`[alt1250.c:register_driver]`), spawns a dedicated RX kthread, registers PM callbacks (`[alt1250.c:g_alt1250pmcb]`), and executes full-duplex SPI DMA/PIO transfers (`[altmdm_spi.c:SPI_EXCHANGE]`) and GPIO handshake lines.

## Verification
- Run: `make test`
