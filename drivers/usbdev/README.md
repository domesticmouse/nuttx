# USB Device Class Drivers (`drivers/usbdev`)

## Overview
Implements the NuttX USB device-side (gadget) class drivers, composite device multiplexer (`composite.c`), FunctionFS-style userspace USB endpoint driver (`usbdev_fs.c`), descriptor and request helpers (`usbdev_desc.c`, `usbdev_req.c`, `usbdev_strings.c`), USB device trace logger (`usbdev_trace.c`, `usbdev_trprintf.c`), and class drivers for CDC-ACM serial (`cdcacm.c`), CDC-ECM Ethernet (`cdcecm.c`), CDC-NCM / CDC-MBIM network (`cdcncm.c`), RNDIS network (`rndis.c`), USB Mass Storage (`usbmsc.c`, `usbmsc_scsi.c`), USB Video Class (`uvc.c`), Android Debug Bridge (`adb.c`), Media Transfer Protocol (`mtp.c`), Device Firmware Upgrade (`dfu.c`), and PL2303 serial emulation (`pl2303.c`).

## Interface
- `[composite.c:composite_initialize]`, `[composite.c:composite_uninitialize]`, `[composite.c:composite_ep0submit]` - Combines multiple USB class drivers into a single composite USB device.
- `[cdcacm.c:cdcacm_initialize]`, `[cdcacm.c:cdcacm_uninitialize]`, `[cdcacm.c:cdcacm_classobject]`, `[cdcacm.c:cdcacm_get_composite_devdesc]`, `[cdcacm.c:cdcacm_write]`, `[cdcacm.c:cdcacm_disable_syslog]` - USB CDC-ACM virtual serial port class driver (`/dev/ttyACM*`).
- `[cdcecm.c:cdcecm_initialize]`, `[cdcecm.c:cdcecm_uninitialize]`, `[cdcecm.c:cdcecm_get_composite_devdesc]`, `[cdcncm.c:cdcncm_initialize]`, `[cdcncm.c:cdcmbim_initialize]`, `[cdcncm.c:cdcncm_get_composite_devdesc]`, `[cdcncm.c:cdcmbim_get_composite_devdesc]`, `[rndis.c:usbdev_rndis_initialize]`, `[rndis.c:usbdev_rndis_set_host_mac_addr]`, `[rndis.c:usbdev_rndis_get_composite_devdesc]` - USB Ethernet/network gadget class drivers (CDC-ECM, CDC-NCM, CDC-MBIM, and RNDIS).
- `[usbmsc.c:usbmsc_configure]`, `[usbmsc.c:usbmsc_bindlun]`, `[usbmsc.c:usbmsc_unbindlun]`, `[usbmsc.c:usbmsc_exportluns]`, `[usbmsc.c:usbmsc_uninitialize]`, `[usbmsc.c:usbmsc_get_composite_devdesc]`, `[usbmsc_scsi.c:usbmsc_scsi_main]`, `[usbmsc_scsi.c:usbmsc_scsi_signal]` - USB Mass Storage Class (Bulk-Only Transport) driver and SCSI worker thread.
- `[usbdev_fs.c:usbdev_fs_initialize]`, `[usbdev_fs.c:usbdev_fs_uninitialize]`, `[usbdev_fs.c:usbdev_fs_classobject]`, `[usbdev_fs.c:usbdev_fs_classuninitialize]` - Userspace USB FunctionFS endpoint character device driver.
- `[uvc.c:usbdev_uvc_initialize]`, `[uvc.c:usbdev_uvc_uninitialize]`, `[uvc.c:usbdev_uvc_classobject]`, `[uvc.c:usbdev_uvc_get_composite_devdesc]` - USB Video Class (UVC) gadget driver.
- `[adb.c:usbdev_adb_initialize]`, `[adb.c:usbdev_adb_uninitialize]`, `[adb.c:usbdev_adb_get_composite_devdesc]`, `[mtp.c:usbdev_mtp_initialize]`, `[mtp.c:usbdev_mtp_uninitialize]`, `[mtp.c:usbdev_mtp_get_composite_devdesc]`, `[dfu.c:usbdev_dfu_initialize]`, `[dfu.c:usbdev_dfu_get_composite_devdesc]`, `[pl2303.c:usbdev_serialinitialize]` - ADB, MTP, DFU, and PL2303 USB device class drivers.
- `[usbdev_desc.c:usbdev_copy_devdesc]`, `[usbdev_desc.c:usbdev_copy_epdesc]`, `[usbdev_req.c:usbdev_allocreq]`, `[usbdev_req.c:usbdev_freereq]`, `[usbdev_trace.c:usbtrace]`, `[usbdev_trace.c:usbtrace_enumerate]`, `[usbdev_trprintf.c:usbtrace_trprintf]` - Descriptor formatting, endpoint request buffer allocation, and USB trace ring-buffer utilities.

## Invariants
- `[composite.c:composite_initialize]` asserts `DEBUGASSERT(pdevices != NULL && ndevices <= NUM_DEVICES_TO_HANDLE)`.
- `[usbmsc.c:usbmsc_configure]` and `[usbmsc_scsi.c:usbmsc_scsi_main]` require `CONFIG_USBMSC_EP0MAXPACKET == dev->ep0->maxpacket`, a locked `priv->thlock` mutex during state transitions (`DEBUGASSERT(nxmutex_is_locked(&priv->thlock))`), and worker thread state `USBMSC_STATE_TERMINATED` or `USBMSC_STATE_NOTSTARTED` prior to teardown.
- `[pl2303.c:usbdev_serialinitialize]` asserts `DEBUGASSERT(priv->nrdq == 0)` and `DEBUGASSERT(priv->nwrq == CONFIG_PL2303_NWRREQS)` when tearing down endpoint queues.

## Side Effects
- Registers USB class drivers with the lower-half USB device controller (`usbdev_register`), allocates DMA-capable endpoint requests (`EP_ALLOCREQ`, `EP_ALLOCBUFFER`), and submits asynchronous USB transfers (`EP_SUBMIT`).
- Registers VFS character devices (`/dev/ttyACM*`, `/dev/ttyUSB*`, `/dev/uvc*`, FunctionFS nodes), network interfaces (`netdev_register`), and spawns kernel worker threads (`kthread_create` in `usbmsc.c`) or work-queue jobs (`ETHWORK`).

## Verification
- Run: `make test`
