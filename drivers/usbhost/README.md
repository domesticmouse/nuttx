# USB Host Core, Controllers, and Class Drivers (`drivers/usbhost`)

## Overview
Implements the NuttX USB host stack core—including device enumeration (`usbhost_enumerate.c`), function address allocation (`usbhost_devaddr.c`), class driver registration and lookup (`usbhost_registerclass.c`, `usbhost_findclass.c`, `usbhost_drivers.c`), port connection waiter threads (`usbhost_waiter.c`), HID report descriptor parsing (`hid_parser.c`), and USB host tracing (`usbhost_trace.c`)—along with host controller drivers for xHCI (`usbhost_xhci.c`, `usbhost_xhci_pci.c`) and SPI-attached MAX3421E (`usbhost_max3421e.c`), and USB host class drivers for hubs (`usbhost_hub.c`), composite devices (`usbhost_composite.c`), Mass Storage (`usbhost_storage.c`), CDC-ACM (`usbhost_cdcacm.c`), CDC-ECM (`usbhost_cdcecm.c`), CDC-MBIM (`usbhost_cdcmbim.c`), Bluetooth HCI (`usbhost_bthci.c`), FT232R serial (`usbhost_ft232r.c`), HID keyboard/mouse (`usbhost_hidkbd.c`, `usbhost_hidmouse.c`), Xbox controller (`usbhost_xboxcontroller.c`), and USB Video Class (`usbhost_uvc.c`).

## Interface
- `[usbhost_drivers.c:usbhost_drivers_initialize]`, `[usbhost_registerclass.c:usbhost_registerclass]`, `[usbhost_findclass.c:usbhost_findclass]`, `[usbhost_enumerate.c:usbhost_enumerate]` - USB host class registry, VID/PID/class matching, and standard chapter-9 device enumeration.
- `[usbhost_devaddr.c:usbhost_devaddr_initialize]`, `[usbhost_devaddr_create]`, `[usbhost_devaddr_destroy]` - 7-bit USB function address bitmap allocator per root hub.
- `[usbhost_waiter.c:usbhost_waiter_initialize]` - Spawns a kernel waiter thread to monitor root hub port status changes and trigger enumeration.
- `[hid_parser.c:hid_parsereport]`, `[hid_parser.c:hid_getitem]`, `[hid_parser.c:hid_putitem]`, `[hid_parser.c:hid_reportsize]` - USB HID report descriptor parser and bitfield extractor.
- `[usbhost_xhci.c:xhci_initialize]`, `[usbhost_xhci.c:xhci_uninitialize]`, `[usbhost_xhci_pci.c:pci_xhci_init]`, `[usbhost_max3421e.c:max3421e_usbhost_initialize]` - xHCI (MMIO/PCI) and MAX3421E (SPI) USB host controller drivers.
- Class driver initialization entrypoints:
  - `[usbhost_hub.c:usbhost_hub_initialize]`, `[usbhost_composite.c:usbhost_composite]` - USB hub and composite device class drivers.
  - `[usbhost_storage.c:usbhost_msc_initialize]`, `[usbhost_storage.c:usbhost_msc_notifier_setup]`, `[usbhost_storage.c:usbhost_msc_notifier_teardown]`, `[usbhost_storage.c:usbhost_msc_notifier_signal]` - USB Mass Storage Class (`/dev/sda`..`/dev/sdz`) block driver and mount notifier.
  - `[usbhost_cdcacm.c:usbhost_cdcacm_initialize]`, `[usbhost_ft232r.c:usbhost_ft232r_initialize]` - USB CDC-ACM and FTDI FT232R virtual serial port host drivers.
  - `[usbhost_cdcecm.c:usbhost_cdcecm_initialize]`, `[usbhost_cdcmbim.c:usbhost_cdcmbim_initialize]`, `[usbhost_bthci.c:usbhost_bthci_initialize]` - USB CDC-ECM, CDC-MBIM network, and Bluetooth HCI host drivers.
  - `[usbhost_hidkbd.c:usbhost_kbdinit]`, `[usbhost_hidmouse.c:usbhost_mouse_init]`, `[usbhost_xboxcontroller.c:usbhost_xboxcontroller_init]` - USB HID keyboard, HID mouse, and Xbox controller input drivers.
  - `[usbhost_uvc.c:usbhost_uvc_initialize]` - USB Video Class (UVC) camera host driver.
- `[usbhost_trace.c:usbhost_trace1]`, `[usbhost_trace.c:usbhost_trace2]`, `[usbhost_trace.c:usbhost_trenumerate]`, `[usbhost_trace.c:usbhost_trdump]` - USB host event trace logging and dump APIs.

## Invariants
- `[usbhost_enumerate.c:usbhost_enumerate]` asserts `DEBUGASSERT(hport != NULL && hport->drvr != NULL)` and `DEBUGASSERT(hport->funcaddr == 0 && funcaddr != 0)` during address assignment.
- Class driver `connect` and `disconnected` callbacks assert `DEBUGASSERT(!up_interrupt_context())` (for connect) and `DEBUGASSERT(usbclass != NULL)`.
- `[hid_parser.c:hid_parsereport]` asserts `DEBUGASSERT(report && filter && rptinfo)`.
- `[usbhost_max3421e.c:max3421e_usbhost_initialize]` requires a valid lower-half SPI interface (`DEBUGASSERT(lower != NULL && lower->spi != NULL)`).

## Side Effects
- Performs USB control, bulk, interrupt, and isochronous transfers (`DRVR_CTRLIN`, `DRVR_CTRLOUT`, `DRVR_TRANSFER`, `DRVR_ASYNCH`) over host controller rings/channels.
- Dynamically registers and unregisters VFS block drivers (`register_blockdriver` for `/dev/sd*`), character drivers (`register_driver` for `/dev/ttyACM*`, `/dev/ttyUSB*`, `/dev/kbda*`, `/dev/mouse*`, `/dev/xbox*`), network devices (`netdev_register`), and video sensors (`imgsensor_register`) on hotplug events.
- Spawns background polling/waiter kernel threads (`kthread_create`) and schedules deferred disconnection cleanup on `LPWORK`/`HPWORK`.

## Verification
- Run: `make test`
