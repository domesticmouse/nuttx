# MIPI I3C Bus Framework and Drivers (`drivers/i3c`)

## Overview
Implements the NuttX MIPI I3C (Improved Inter-Integrated Circuit) bus master core, Common Command Code (CCC) dispatch, Dynamic Address Assignment (DAA), In-Band Interrupt (IBI) slot pooling and work queue dispatch, legacy I2C device attachment, and `/dev/i3cN` VFS character driver.

## Interface
- `master.c:i3c_master_register`, `master.c:i3c_master_unregister` - Initializes an I3C master controller, performs bus initialization and DAA, and registers the controller with the I3C subsystem.
- `master.c:i3c_master_do_daa`, `master.c:i3c_master_entdaa_locked`, `master.c:i3c_master_enec_locked`, `master.c:i3c_master_disec_locked`, `master.c:i3c_master_send_ccc_cmd_locked`, `master.c:i3c_master_get_free_addr`, `master.c:i3c_master_set_info`, `master.c:i3c_master_add_i3c_dev_locked` - Executes Dynamic Address Assignment, Common Command Codes, and address slot management on an I3C bus.
- `master.c:i3c_master_queue_ibi`, `master.c:i3c_generic_ibi_alloc_pool`, `master.c:i3c_generic_ibi_free_pool`, `master.c:i3c_generic_ibi_get_free_slot`, `master.c:i3c_generic_ibi_recycle_slot` - Manages In-Band Interrupt (IBI) payload slot pools and queues IBI events to the work queue.
- `master.c:i3c_master_i2c_attach`, `master.c:i3c_master_detach_i2c_dev` - Attaches and detaches legacy I2C devices on an I3C bus.
- `device.c:i3c_device_do_priv_xfers`, `device.c:i3c_device_send_ccc_cmd`, `device.c:i3c_device_get_info`, `device.c:i3c_device_request_ibi`, `device.c:i3c_device_free_ibi`, `device.c:i3c_device_enable_ibi`, `device.c:i3c_device_disable_ibi`, `device.c:i3c_master_find_i3c_dev` - High-level I3C device API for private SDR transfers, CCC commands, and IBI lifecycle management.
- `i3c_driver.c:i3c_register`, `i3c_driver.c:i3c_driver_s` - Registers the `/dev/i3cN` character device supporting `I3CIOC_PRIV_XFERS`, `I3CIOC_SEND_CCC_CMD`, and IBI `ioctl` requests.
- `internals.h:i3c_bus_normaluse_lock`, `internals.h:i3c_bus_normaluse_unlock`, `internals.h:i3c_dev_do_priv_xfers_locked` - Internal bus locking and locked device operation helpers.

## Invariants
- `i3c_driver.c:i3c_register` asserts `master != NULL` and `(unsigned)bus < 1000`.
- All `*_locked` functions in `master.c` and `internals.h` require the caller to hold the I3C bus lock (`i3c_bus_normaluse_lock` / `i3c_bus_maintenance_lock` via `nxmutex_lock`).
- `device.c:i3c_device_request_ibi` requires `req->handler != NULL` and `req->num_slots > 0`, returning `-EINVAL` otherwise.

## Side Effects
- Acquires bus mutexes (`nxmutex_lock` in `master.c:i3c_bus_normaluse_lock`, `device.c:i3c_device_do_priv_xfers`), IBI semaphores (`nxsem_wait`), and IRQ spinlocks (`spin_lock_irqsave` in `master.c:i3c_master_queue_ibi`).
- Executes hardware I3C bus initialization, DAA, CCC broadcasts, and SDR transfers via controller `master->ops` callbacks (`master.c:i3c_master_register`).
- Schedules IBI handlers on the kernel work queue (`work_queue` in `master.c:i3c_master_queue_ibi`), allocates descriptors via `kmm_zalloc`, and registers `/dev/i3cN` via `register_driver` (`i3c_driver.c:i3c_register`).

## Verification
- Run: `make test`
