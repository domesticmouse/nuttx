# Vhost Virtual Device Framework and Backend Drivers (`drivers/vhost`)

## Overview
Implements the NuttX Virtio Host (`vhost`) bus framework (`vhost.c`) and host-side backend drivers for block storage (`vhost-blk.c`), CAN (`vhost-can.c`), I2C (`vhost-i2c.c`), networking (`vhost-net.c`), random number generation (`vhost-rng.c`), Replay Protected Memory Block (`vhost-rpmb.c`), RPMSG (`vhost-rpmsg.c`), and serial ports (`vhost-serial.c`).

## Interface
- `[vhost.c:vhost_register_drivers]`, `[vhost.c:vhost_register_driver]`, `[vhost.c:vhost_unregister_driver]`, `[vhost.c:vhost_register_device]`, `[vhost.c:vhost_unregister_device]` - Core vhost bus registration and matching routines for host devices and backend drivers.
- `[vhost.c:vhost_get_vq_buffers]`, `[vhost.c:vhost_get_vq_buffers_pa]` - Extracts contiguous or scatter-gather buffer descriptors from a vhost virtqueue (`struct virtqueue`).
- Backend driver registration functions:
  - `[vhost-blk.c:vhost_register_blk_driver]` - Host block device backend (`VIRTIO_ID_BLOCK`).
  - `[vhost-can.c:vhost_register_can_driver]` - Host CAN controller backend (`VIRTIO_ID_CAN`).
  - `[vhost-i2c.c:vhost_register_i2c_driver]` - Host I2C master backend (`VIRTIO_ID_I2C`).
  - `[vhost-net.c:vhost_register_net_driver]` - Host network interface backend (`VIRTIO_ID_NET`).
  - `[vhost-rng.c:vhost_register_rng_driver]` - Host entropy/RNG backend (`VIRTIO_ID_RNG`).
  - `[vhost-rpmb.c:vhost_register_rpmb_driver]` - Host RPMB backend (`VIRTIO_ID_RPMB`).
  - `[vhost-rpmsg.c:vhost_register_rpmsg_driver]` - Host RPMSG backend (`VIRTIO_ID_RPMSG`).
  - `[vhost-serial.c:vhost_register_serial_driver]` - Host console/serial backend (`VIRTIO_ID_CONSOLE`).

## Invariants
- `[vhost.c:vhost_register_driver]` asserts `DEBUGASSERT(driver != NULL && driver->probe != NULL && driver->remove != NULL)`.
- `[vhost.c:vhost_get_vq_buffers]` and `[vhost.c:vhost_get_vq_buffers_pa]` assert `DEBUGASSERT(vb != NULL && vbsize >= 1 && vbcnt != NULL)`.

## Side Effects
- `[vhost.c:vhost_register_device]` and `[vhost.c:vhost_register_driver]` acquire the global `g_vhost_bus.lock` mutex (`nxmutex_lock`), match devices by `device->id.device == driver->device`, invoke `driver->probe`, and schedule deferred probing on `LPWORK` (`work_queue`) if probe returns `-ENOENT`.
- Backend drivers open local VFS block/char devices or register network/serial interfaces, process guest virtqueue descriptors (`virtqueue_get_buffer`, `virtqueue_add_consumed_buffer`), and kick guest virtqueues (`virtqueue_kick`).

## Verification
- Run: `make test`
