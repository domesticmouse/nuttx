# Broadcom / Cypress BCM43xxx FullMAC Wi-Fi Driver (`drivers/wireless/ieee80211/bcm43xxx`)

## Overview
Implements the FullMAC IEEE 802.11 Wi-Fi driver for Broadcom/Cypress BCM43xxx and CYW43439 chipsets (`4301x`, `43362`, `43438`, `43439`, `43455`). Includes SDIO and gSPI bus transports (`bcmf_sdio.c`, `bcmf_gspi.c`, `bcmf_gspi_f2_frame.c`), Silicon Backplane core initialization and firmware/NVRAM/CLM upload (`bcmf_core.c`, `bcmf_driver.c`), SDPCM/BDC/CDC protocol framing (`bcmf_sdpcm.c`, `bcmf_bdc.c`, `bcmf_cdc.c`, `bcmf_interface.c`), and the NuttX `wlanN` network interface and Wireless Extensions (`iwconfig`) layer (`bcmf_netdev.c`).

## Interface
- `[bcmf_sdio.c:bcmf_sdio_initialize]`, `[bcmf_gspi.c:bcmf_gspi_initialize]` - Initializes a BCM43xxx device over SDIO or gSPI and spawns the bus daemon thread.
- `[bcmf_driver.c:bcmf_driver_initialize]`, `[bcmf_driver.c:bcmf_wl_enable]`, `[bcmf_driver.c:bcmf_wl_active]`, `[bcmf_driver.c:bcmf_wl_set_mac_address]`, `[bcmf_driver.c:bcmf_wl_set_country_code]`, `[bcmf_driver.c:bcmf_wl_set_dtim]`, `[bcmf_driver.c:bcmf_wl_start_scan]`, `[bcmf_driver.c:bcmf_wl_get_scan_results]` - Core wireless configuration, CLM blob download, AP/STA association, and scan state machines.
- `[bcmf_netdev.c:bcmf_netdev_register]`, `[bcmf_netdev.c:bcmf_netdev_alloc_tx_frame]`, `[bcmf_netdev.c:bcmf_netdev_notify_tx]`, `[bcmf_netdev.c:bcmf_netdev_notify_rx]` - Registers the `wlanN` network device and handles Ethernet frame TX/RX and `SIOCSIW*`/`SIOCGIW*` ioctls.
- `[bcmf_core.c:bcmf_core_upload_firmware]`, `[bcmf_core.c:bcmf_core_isup]`, `[bcmf_core.c:bcmf_core_reset]`, `[bcmf_core.c:bcmf_core_disable]`, `[bcmf_core.c:bcmf_read_sbreg]`, `[bcmf_core.c:bcmf_write_sbreg]` - Silicon Backplane window management, core reset, and firmware/NVRAM upload.
- `[bcmf_sdpcm.c:bcmf_sdpcm_readframe]`, `[bcmf_sdpcm.c:bcmf_sdpcm_sendframe]`, `[bcmf_sdpcm.c:bcmf_sdpcm_queue_frame]`, `[bcmf_sdpcm.c:bcmf_sdpcm_free_frame]`, `[bcmf_gspi_f2_frame.c:bcmf_gspi_read_f2_frame]`, `[bcmf_gspi_f2_frame.c:bcmf_gspi_send_f2_frame]` - SDPCM and gSPI F2 frame multiplexing and flow control.
- `[bcmf_cdc.c:bcmf_cdc_ioctl]`, `[bcmf_cdc.c:bcmf_cdc_iovar_request]`, `[bcmf_cdc.c:bcmf_cdc_iovar_request_unsafe]`, `[bcmf_cdc.c:bcmf_cdc_process_control_frame]` - Control Channel (CDC) ioctl and IOVAR request/response serialization.
- `[bcmf_bdc.c:bcmf_bdc_transmit_frame]`, `[bcmf_bdc.c:bcmf_bdc_process_event_frame]`, `[bcmf_bdc.c:bcmf_event_register]`, `[bcmf_bdc.c:bcmf_event_unregister]`, `[bcmf_bdc.c:bcmf_event_push_config]` - Bulk Data Channel (BDC) header encapsulation and asynchronous firmware event dispatcher.
- `[bcmf_gpio.c:bcmf_set_gpio]`, `[bcmf_gpio.c:bcmf_get_gpio]`, `[bcmf_utils.c:bcmf_hexdump]` - Chip GPIO IOVAR control and diagnostic hex dump utility.

## Invariants
- `[bcmf_gspi.c:bcmf_transfer_bytes]` asserts 32-bit buffer alignment (`DEBUGASSERT((((uintptr_t)buf) & 3) == 0)`).
- `[bcmf_cdc.c:bcmf_cdc_control_request]` serializes control requests using `bus->control_mutex` (`nxsem_wait_uninterruptible`) and waits for matching `reqid` completion within `BCMF_CONTROL_TIMEOUT_MS`.

## Side Effects
- Performs SDIO CMD52/CMD53 or gSPI register/FIFO transfers, uploads firmware/NVRAM/CLM images to chip RAM, and attaches out-of-band (OOB) GPIO interrupts.
- Spawns the `bcmf` bus processing kernel thread (`kthread_create`), schedules low-power and network work on `LPWORK`, and registers `wlanN` network interfaces via `netdev_register`.

## Verification
- Run: `make test`
