# NuttX Virtual Host (vhost) Framework (`include/nuttx/vhost`)

## Overview
Provides the NuttX Virtual Host (`vhost`) device and driver framework built on OpenAMP VirtIO, allowing NuttX to act as the host-side backend processor servicing virtqueues shared with guest/remote VirtIO devices.

## Interface
- `vhost.h:vhost_device`, `vhost.h:vhost_driver`, `vhost.h:vhost_buf_s` - Vhost device alias (`struct virtio_device`), backend driver descriptor (`device`, `probe`, `remove`, `node`), and scatter-gather buffer descriptor.
- `vhost.h:vhost_register_device`, `vhost.h:vhost_unregister_device`, `vhost.h:vhost_register_driver`, `vhost.h:vhost_unregister_driver`, `vhost.h:vhost_register_drivers` - Vhost device and driver registration lifecycle APIs.
- `vhost.h:vhost_get_vq_buffers`, `vhost.h:vhost_get_vq_buffers_pa`, `vhost.h:up_vhost_iomap` - Virtqueue descriptor chain extraction and guest-physical-to-host-virtual address translation helpers.
- `vhost.h:vhost_create_virtqueues`, `vhost.h:vhost_delete_virtqueues`, `vhost.h:vhost_get_status`, `vhost.h:vhost_set_status`, `vhost.h:vhost_get_features`, `vhost.h:vhost_set_features`, `vhost.h:vhost_has_feature`, `vhost.h:vhost_read_config`, `vhost.h:vhost_write_config`, `vhost.h:vhost_read_config_member`, `vhost.h:vhost_write_config_member` - Dispatch macros wrapping OpenAMP VirtIO transport and configuration operations.

## Invariants
- A `vhost.h:vhost_device` registered via `vhost.h:vhost_register_device` is only bound (`probe`) to a matching `vhost.h:vhost_driver` after the guest driver sets `VIRTIO_CONFIG_STATUS_DRIVER_OK` in the device status register.

## Side Effects
- `vhost.h:vhost_register_device` and `vhost.h:vhost_register_driver` mutate the kernel's global vhost device/driver lists and invoke matching `probe` callbacks.
- `vhost.h:vhost_get_vq_buffers` consumes available descriptor indices from the shared virtqueue ring and translates guest physical addresses via `vhost.h:up_vhost_iomap`.

## Verification
- Run: `make test`
