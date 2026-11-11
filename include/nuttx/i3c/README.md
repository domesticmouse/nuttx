# MIPI I3C Bus Subsystem Headers (`include/nuttx/i3c`)

## Overview
Defines the MIPI Improved Inter-Integrated Circuit (`i3c`) bus subsystem for NuttX, including Common Command Codes (`ccc.h`), I3C device discovery and dynamic address assignment (DAA), In-Band Interrupt (IBI) slot pools, legacy I2C device attachment on I3C buses, master controller operations (`master.h`), and userspace character driver `ioctl` interfaces (`i3c_driver.h`).

## Interface
- `ccc.h:i3c_ccc_cmd`, `ccc.h:i3c_ccc_cmd_dest`, `ccc.h:i3c_ccc_cmd_payload`, `ccc.h:i3c_ccc_events`, `ccc.h:i3c_ccc_mwl`, `ccc.h:i3c_ccc_mrl`, `ccc.h:i3c_ccc_dev_desc`, `ccc.h:i3c_ccc_defslvs`, `ccc.h:I3C_CCC_ENEC`, `ccc.h:I3C_CCC_DISEC`, `ccc.h:I3C_CCC_RSTDAA`, `ccc.h:I3C_CCC_ENTDAA`, `ccc.h:I3C_CCC_SETDASA`, `ccc.h:I3C_CCC_GETPID`, `ccc.h:I3C_CCC_GETBCR`, `ccc.h:I3C_CCC_GETDCR`, `ccc.h:I3C_CCC_GETSTATUS` - MIPI I3C broadcast and direct Common Command Code (CCC) opcodes and payload structures.
- `device.h:i3c_device`, `device.h:i3c_device_id`, `device.h:i3c_device_info`, `device.h:i3c_priv_xfer`, `device.h:i3c_ibi_setup`, `device.h:i3c_ibi_payload`, `device.h:i3c_error_code`, `device.h:i3c_hdr_mode` - Client device descriptors, Provisional ID (PID) / Bus Characteristics Register (BCR) macros, private SDR/HDR transfer structures, and IBI setup parameters.
- `device.h:i3c_device_do_priv_xfers`, `device.h:i3c_device_get_info`, `device.h:i3c_device_enable_ibi`, `device.h:i3c_device_disable_ibi`, `device.h:i3c_device_request_ibi`, `device.h:i3c_device_free_ibi`, `device.h:i3c_device_send_ccc_cmd`, `device.h:i3c_master_find_i3c_dev`, `device.h:i3c_master_i2c_attach`, `device.h:i3c_master_detach_i2c_dev` - Device-level transfer, IBI lifecycle, CCC dispatch, and I2C compatibility APIs.
- `master.h:i3c_master_controller`, `master.h:i3c_master_controller_ops`, `master.h:i3c_bus`, `master.h:i3c_dev_desc`, `master.h:i2c_dev_desc`, `master.h:i3c_ibi_slot`, `master.h:i3c_master_register`, `master.h:i3c_master_unregister`, `master.h:i3c_master_do_daa`, `master.h:i3c_master_entdaa_locked`, `master.h:i3c_master_defslvs_locked`, `master.h:i3c_master_enec_locked`, `master.h:i3c_master_disec_locked`, `master.h:i3c_master_queue_ibi`, `master.h:i3c_generic_ibi_alloc_pool`, `master.h:i3c_generic_ibi_free_pool` - Master controller bus management, Dynamic Address Assignment (DAA), and generic IBI slot pool routines.
- `i3c_driver.h:i3c_transfer_s`, `i3c_driver.h:i3c_register`, `i3c_driver.h:I3CIOC_PRIV_XFERS`, `i3c_driver.h:I3CIOC_EN_IBI`, `i3c_driver.h:I3CIOC_DIS_IBI`, `i3c_driver.h:I3CIOC_REQ_IBI`, `i3c_driver.h:I3CIOC_FREE_IBI`, `i3c_driver.h:I3CIOC_GET_DEVINFO` - Userspace I3C character driver registration and `ioctl` commands.

## Invariants
- Functions suffixed with `_locked` in `master.h` (`i3c_master_disec_locked`, `i3c_master_enec_locked`, `i3c_master_entdaa_locked`, `i3c_master_defslvs_locked`, `i3c_master_add_i3c_dev_locked`, `i3c_master_send_ccc_cmd_locked`) require the caller to hold the I3C bus lock.
- Dynamic addresses on the bus are bounded by `master.h:I3C_MAX_ADDR` (`0x7f`), with `I3C_HOT_JOIN_ADDR` (`0x02`) and `I3C_BROADCAST_ADDR` (`0x7e`) reserved by the MIPI I3C specification.

## Side Effects
- `master.h:i3c_master_register` and `i3c_driver.h:i3c_register` initialize the I3C bus topology, perform bus initialization/DAA, and register `/dev/i3c*` character device nodes.
- `master.h:i3c_master_queue_ibi` schedules IBI handler execution on the kernel workqueue (`struct work_s`).

## Verification
- Run: `make test`
