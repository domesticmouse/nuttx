# Field-Oriented Control (FOC) Motor Drivers (`drivers/motor/foc`)

## Overview
Implements the Field-Oriented Control (FOC) character device upper-half framework, power-stage gate driver abstractions, DRV8301 3-phase gate driver, and simulated FOC dummy lower-half driver.

## Interface
- `[foc_dev.c:foc_register]` - Registers a `/dev/focN` character device bound to a `struct foc_lower_s` implementation (`[foc_dev.c:g_foc_fops]`, `[foc_dev.c:g_foc_callbacks]`).
- `[foc_pwr.c:focpwr_initialize]` - Initializes a FOC power-stage/gate-driver device (`struct focpwr_dev_s`).
- `[drv8301.c:drv8301_register]` - Registers the TI DRV8301 3-phase gate driver over SPI (`[drv8301.c:struct drv8301_priv_s]`).
- `[foc_dummy.c:foc_dummy_initialize]`, `[foc_dummy.c:foc_dummy_update]` - Simulated FOC lower-half driver for testing without physical motor hardware (`[foc_dummy.c:struct foc_dummy_data_s]`).

## Invariants
- Opening `/dev/focN` with `O_NONBLOCK` is rejected with `-EPERM` (`[foc_dev.c:foc_open]`), and all mandatory `struct foc_lower_ops_s` callbacks are verified via `[foc_dev.c:foc_lower_ops_assert]`.
- Real-time current/voltage notifier synchronization uses an uninterruptible semaphore (`[foc_dev.c:nxsem_wait_uninterruptible]`) and mutex lock (`[foc_dev.c:nxmutex_lock]`).

## Side Effects
- Registers VFS character devices (`register_driver`), drives PWM/ADC lower-half hardware for 3-phase motor control, and communicates with gate drivers via SPI (`[drv8301.c:SPI_SEND]`).

## Verification
- Run: `make test`
