# I2C Drivers and Multiplexers (`drivers/i2c`)

## Overview
Provides the NuttX I2C master and slave VFS character drivers (`/dev/i2c*`, `/dev/i2cslv*`), high-level I2C transfer helper functions (`i2c_read`, `i2c_write`, `i2c_writeread`), software bit-bang I2C master drivers (including GPIO I/O expander bit-banging), and I2C bus multiplexer drivers (PCA9540BDP, TCA9548A).

## Interface
- `i2c_driver.c:i2c_register`, `i2c_driver.c:i2c_driver_s` - Registers an I2C master character driver at `/dev/i2cN` supporting `I2CIOC_TRANSFER` and `I2CIOC_RESET`.
- `i2c_slave_driver.c:i2c_slave_register`, `i2c_slave_driver.c:i2c_slave_driver_s` - Registers an I2C slave character driver at `/dev/i2cslvN` supporting buffered `read`, `write`, `poll`, and `unlink`.
- `i2c_read.c:i2c_read`, `i2c_write.c:i2c_write`, `i2c_writeread.c:i2c_writeread` - Convenience wrappers that construct `i2c_msg_s` descriptors and invoke `I2C_TRANSFER`.
- `i2c_bitbang.c:i2c_bitbang_initialize`, `i2c_bitbang.c:i2c_bitbang_dev_s`, `i2c_bitbang_ioexpander.c:i2c_bitbang_ioexpander_initialize`, `i2c_bitbang_ioexpander.c:i2c_bb_ioe_s` - Software bit-banged I2C master implementation and I/O expander pin adapter.
- `pca9540bdp.c:pca9540bdp_initialize`, `pca9540bdp.c:pca9540bdp_lower_half`, `pca9540bdp.h:pca9540bdp_dev_s` - Initializes the NXP PCA9540BDP 2-channel I2C multiplexer and exposes per-port virtual `i2c_master_s` lower halves.
- `tca9548a.c:tca9548a_initialize`, `tca9548a.c:tca9548a_lower_half`, `tca9548a.c:i2c_channel_dev_s` - Initializes the TI TCA9548A 8-channel I2C switch and exposes per-channel virtual `i2c_master_s` lower halves.

## Invariants
- `i2c_driver.c:i2c_register` asserts `i2c != NULL && (unsigned)bus < 1000`; `i2c_slave_driver.c:i2c_slave_register` asserts `dev != NULL && (unsigned int)bus < 100`.
- `i2c_writeread.c:i2c_writeread` asserts `config->addrlen == 10 || config->addrlen == 7`.
- `i2c_bitbang.c:i2c_bitbang_initialize` asserts `lower != NULL && lower->ops != NULL`.
- `pca9540bdp.c:pca9540bdp_initialize` and `tca9548a.c:tca9548a_initialize` assert `i2c != NULL` and `dev != NULL`.

## Side Effects
- Executes hardware and bit-banged I2C bus transactions via `I2C_TRANSFER` and `I2C_RESET` (`i2c_driver.c:i2c_register`, `i2c_read.c:i2c_read`, `i2c_write.c:i2c_write`, `i2c_writeread.c:i2c_writeread`).
- Acquires mutexes (`nxmutex_lock` in `i2c_driver.c:i2c_register`), semaphores (`nxsem_wait` in `i2c_slave_driver.c:i2c_slave_register`), and IRQ-saving spinlocks (`spin_lock_irqsave` in `i2c_bitbang.c:i2c_bitbang_initialize`, `i2c_slave_driver.c:i2c_slave_register`).
- Registers VFS character devices via `register_driver` and allocates driver structures on the kernel heap via `kmm_zalloc` and `kmm_malloc` (`i2c_driver.c:i2c_register`, `i2c_slave_driver.c:i2c_slave_register`, `pca9540bdp.c:pca9540bdp_initialize`, `tca9548a.c:tca9548a_initialize`).

## Verification
- Run: `make test`
