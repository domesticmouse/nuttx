# I2C Bus Subsystem Headers (`include/nuttx/i2c`)

## Overview
Defines the NuttX Inter-Integrated Circuit (`i2c`) master and slave bus abstractions, transfer message descriptors, bit-banging lower-half helpers (direct and GPIO-expander-backed), character driver registration, and I2C bus multiplexers/switches (PCA9540BDP, TCA9548A).

## Interface
- `i2c_master.h:i2c_master_s`, `i2c_master.h:i2c_ops_s`, `i2c_master.h:i2c_msg_s`, `i2c_master.h:i2c_config_s`, `i2c_master.h:i2c_transfer_s` - Core I2C master device handle, operation vtable (`transfer`, `reset`, `setup`, `shutdown`), transaction message descriptor, and client configuration structures.
- `i2c_master.h:I2C_TRANSFER`, `i2c_master.h:I2C_RESET`, `i2c_master.h:I2C_SETUP`, `i2c_master.h:I2C_SHUTDOWN`, `i2c_master.h:i2c_register`, `i2c_master.h:i2c_write`, `i2c_master.h:i2c_read`, `i2c_master.h:i2c_writeread` - Master bus dispatch macros, character driver registration (`/dev/i2c*`), and convenience transfer wrappers.
- `i2c_master.h:I2CIOC_TRANSFER`, `i2c_master.h:I2CIOC_RESET`, `i2c_master.h:I2C_M_READ`, `i2c_master.h:I2C_M_TEN`, `i2c_master.h:I2C_M_NOSTOP`, `i2c_master.h:I2C_M_NOSTART`, `i2c_master.h:I2C_SPEED_STANDARD`, `i2c_master.h:I2C_SPEED_FAST`, `i2c_master.h:I2C_SPEED_FAST_PLUS`, `i2c_master.h:I2C_SPEED_HIGH` - `ioctl` commands, message flags, and standard bus frequencies.
- `i2c_slave.h:i2c_slave_s`, `i2c_slave.h:i2c_slaveops_s`, `i2c_slave.h:i2c_slave_callback_t`, `i2c_slave.h:i2c_slave_complete_t`, `i2c_slave.h:i2c_slave_register`, `i2c_slave.h:I2CS_SETOWNADDRESS`, `i2c_slave.h:I2CS_WRITE`, `i2c_slave.h:I2CS_READ`, `i2c_slave.h:I2CS_REGISTERCALLBACK` - I2C slave peripheral abstraction and character driver registration.
- `i2c_bitbang.h:i2c_bitbang_lower_ops_s`, `i2c_bitbang.h:i2c_bitbang_lower_dev_s`, `i2c_bitbang.h:i2c_bitbang_initialize`, `i2c_bitbang_ioexpander.h:i2c_bitbang_ioexpander_initialize` - Software bit-banged I2C master implementation over raw SCL/SDA callbacks or an `ioexpander_dev_s`.
- `pca9540bdp.h:pca9540bdp_dev_s`, `pca9540bdp.h:pca9540bdp_initialize`, `pca9540bdp.h:pca9540bdp_lower_half`, `tca9548a.h:tca9548a_dev_s`, `tca9548a.h:tca9548a_initialize`, `tca9548a.h:tca9548a_lower_half` - 2-channel PCA9540BDP and 8-channel TCA9548A I2C bus multiplexer drivers exposing per-port virtual `i2c_master_s` instances.

## Invariants
- `i2c_master.h:i2c_config_s.addrlen` must be `7` or `10`; 10-bit addresses require `I2C_M_TEN` in `i2c_msg_s.flags`.
- `i2c_master.h:I2C_TRANSFER` executes an array of `i2c_msg_s` messages atomically with respect to other threads sharing the same `i2c_master_s` bus controller.

## Side Effects
- `i2c_master.h:i2c_register` and `i2c_slave.h:i2c_slave_register` register character devices in the VFS.
- `i2c_master.h:I2C_TRANSFER`, `i2c_master.h:I2C_RESET`, and `i2c_bitbang.h:i2c_bitbang_lower_ops_s` drive physical SCL/SDA bus lines and peripheral controller hardware.

## Verification
- Run: `make test`
