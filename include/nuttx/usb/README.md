# NuttX USB Host, Device & Type-C Subsystem (`include/nuttx/usb`)

## Overview
Provides the USB 2.0/3.0 protocol specification descriptors (`usb.h`), USB Device (`usbdev.h`) and composite device (`composite.h`) controller/class frameworks, USB Host (`usbhost.h`) controller/class frameworks, host controller register definitions (`ehci.h`, `ohci.h`, `xhci.h`, `xhci_pci.h`, `max3421e.h`), USB device/host class headers (CDC-ACM, CDC-ECM, CDC-NCM, MSC, HID, UVC, Audio, DFU, MTP, RNDIS, ADB, Hub, PL2303), USB Type-C/PD controllers (`fusb301.h`, `fusb302.h`, `fusb303.h`, `stusb4500.h`), and USB trace/monitoring utilities (`usbdev_trace.h`, `usbhost_trace.h`, `usbmonitor.h`).

## Interface
- `usb.h:usb_ctrlreq_s`, `usb.h:usb_devdesc_s`, `usb.h:usb_cfgdesc_s`, `usb.h:usb_ifdesc_s`, `usb.h:usb_epdesc_s`, `usb.h:usb_ss_epcompdesc_s` - Standard USB control request and descriptor structures.
- `usbdev.h:usbdev_s`, `usbdev.h:usbdev_ops_s`, `usbdev.h:usbdev_ep_s`, `usbdev.h:usbdev_epops_s`, `usbdev.h:usbdev_req_s`, `usbdev.h:usbdev_classdriver_s`, `usbdev.h:usbdev_register`, `usbdev.h:usbdev_unregister`, `usbdev.h:usbdev_allocreq`, `usbdev.h:usbdev_freereq`, `usbdev.h:EP_CONFIGURE`, `usbdev.h:EP_SUBMIT`, `usbdev.h:EP_CANCEL` - USB Device controller and class driver framework.
- `composite.h:composite_initialize`, `composite.h:composite_uninitialize`, `composite.h:composite_ep0submit`, `usbdev.h:composite_devdesc_s` - Multi-interface USB composite device orchestration.
- `usbhost.h:usbhost_driver_s`, `usbhost.h:usbhost_connection_s`, `usbhost.h:usbhost_class_s`, `usbhost.h:usbhost_hubport_s`, `usbhost.h:usbhost_ep_t`, `usbhost.h:usbhost_registerclass`, `usbhost.h:usbhost_findclass`, `usbhost.h:DRVR_ALLOC`, `usbhost.h:DRVR_TRANSFER`, `usbhost.h:DRVR_ASYNCH`, `usbhost_devaddr.h:usbhost_devaddr_create` - USB Host controller, hub port enumeration, and class driver framework.
- Host Controllers: `ehci.h:ehci_qh_s`, `ehci.h:ehci_qtd_s`, `ohci.h:ohci_ed_s`, `ohci.h:ohci_gtd_s`, `xhci.h:xhci_initialize`, `xhci_pci.h:pci_xhci_init`, `max3421e.h:max3421e_usbhost_initialize`.
- Device & Host Classes: `cdc.h:cdc_acm_funcdesc_s`, `cdcacm.h:cdcacm_initialize`, `cdcecm.h:cdcecm_initialize`, `cdcncm.h:cdcncm_initialize`, `storage.h:usbmsc_cbw_s`, `usbmsc.h:usbmsc_configure`, `usbmsc.h:usbmsc_bindlun`, `usbmsc.h:usbmsc_exportluns`, `hid.h:usbhid_descriptor_s`, `hid_parser.h:hid_parsereport`, `uvc.h:usbdev_uvc_initialize`, `audio.h:adc_ac_ifdesc_s`, `dfu.h:usbdev_dfu_get_composite_devdesc`, `mtp.h:usbdev_mtp_initialize`, `rndis.h:usbdev_rndis_initialize`, `adb.h:usbdev_adb_initialize`, `hub.h:usb_hubdesc_s`, `pl2303.h:usbdev_serialinitialize`.
- USB Type-C & Trace: `fusb301.h:fusb301_register`, `fusb302.h:fusb302_register`, `fusb303.h:fusb303_register`, `stusb4500.h:stusb4500_register`, `usbdev_trace.h:usbtrace`, `usbhost_trace.h:usbhost_trace1`, `usbmonitor.h:usbmonitor_start`.

## Invariants
- Buffers used for USB host or device transfers (`usbdev.h:usbdev_req_s`, `usbhost.h:DRVR_TRANSFER`) must be allocated via `DEV_ALLOCBUFFER` / `usbdev_dma_alloc` or `DRVR_ALLOC` to satisfy hardware DMA alignment and cache-line constraints.
- Multi-LUN USB mass storage initialization must follow the strict sequence `usbmsc.h:usbmsc_configure` -> one or more `usbmsc.h:usbmsc_bindlun` calls -> `usbmsc.h:usbmsc_exportluns`.

## Side Effects
- Initializing USB device or host classes (`cdcacm.h:cdcacm_initialize`, `cdcecm.h:cdcecm_initialize`, `usbhost.h:usbhost_msc_initialize`) registers VFS character/block devices (`/dev/ttyACM*`, `/dev/sda*`) or network interfaces (`eth*`) and enables USB pull-up resistors or host port power.
- `usbdev.h:EP_SUBMIT` and `usbhost.h:DRVR_TRANSFER` program endpoint DMA descriptors and trigger USB bus transactions.

## Verification
- Run: `make test`
