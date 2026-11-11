# NuttX VirtIO Device & Driver Framework (`include/nuttx/virtio`)

## Overview
Provides the NuttX VirtIO device, driver, and virtqueue management interfaces built on OpenAMP (`virtio.h`, `virtio-config.h`), MMIO and PCI transport bindings (`virtio-mmio.h`, `virtio-pci.h`), and standard VirtIO device protocol/configuration headers for block (`virtio-blk.h`), CAN (`virtio-can.h`), I2C (`virtio-i2c.h`), Replay Protected Memory Block (`virtio-rpmb.h`), and serial (`virtio-serial.h`) devices.

## Interface
- `virtio.h:virtio_driver`, `virtio.h:virtio_register_driver`, `virtio.h:virtio_unregister_driver`, `virtio.h:virtio_register_device`, `virtio.h:virtio_unregister_device`, `virtio.h:virtio_register_drivers`, `virtio.h:virtio_alloc_buf`, `virtio.h:virtio_free_buf` - VirtIO driver registration, device discovery, DMA buffer allocation, and spinlock-synchronized `virtqueue_*_lock` wrappers (`virtqueue_add_buffer_lock`, `virtqueue_get_buffer_lock`, `virtqueue_kick_lock`).
- `virtio-config.h:virtio_read_config`, `virtio-config.h:virtio_write_config`, `virtio-config.h:virtio_read_config_member`, `virtio-config.h:virtio_write_config_member`, `virtio-config.h:VIRTIO_F_ANY_LAYOUT` - VirtIO device configuration space read/write helpers.
- `virtio-mmio.h:virtio_register_mmio_device`, `virtio-mmio.h:virtio_register_mmio_device_secure`, `virtio-pci.h:register_virtio_pci_driver` - Memory-mapped I/O and PCI VirtIO transport registration.
- `virtio-blk.h:virtio_blk_req_s`, `virtio-blk.h:virtio_blk_resp_s`, `virtio-blk.h:virtio_blk_config_s`, `virtio-blk.h:vhost_blk_config_s` - VirtIO block request/response headers and capacity configuration.
- `virtio-can.h:virtio_can_config_s`, `virtio-can.h:virtio_can_tx_out_s`, `virtio-can.h:virtio_can_rx_s`, `virtio-can.h:virtio_can_control_out_s` - VirtIO CAN frame and controller state structures.
- `virtio-i2c.h:virtio_i2c_out_hdr_s`, `virtio-i2c.h:virtio_i2c_in_hdr_s`, `virtio-i2c.h:vhost_i2c_config_s` - VirtIO I2C transaction headers.
- `virtio-rpmb.h:virtio_rpmb_frame`, `virtio-rpmb.h:virtio_rpmb_config_s`, `virtio-serial.h:virtio_serial_config_s`, `virtio-serial.h:vhost_serial_config_s` - VirtIO RPMB frame and VirtIO console/serial configuration structures.

## Invariants
- Concurrent accesses to a shared `struct virtqueue` must be serialized using the `virtio.h:virtqueue_*_lock` inline helpers passing the associated `spinlock_t *lock` unless external mutual exclusion is held.
- Protocol wire structures (`virtio-blk.h:virtio_blk_req_s`, `virtio-can.h:virtio_can_tx_out_s`, `virtio-i2c.h:virtio_i2c_out_hdr_s`, `virtio-rpmb.h:virtio_rpmb_frame`) are packed (`begin_packed_struct`) to match the OASIS VirtIO specification layout.

## Side Effects
- `virtio-mmio.h:virtio_register_mmio_device` and `virtio-pci.h:register_virtio_pci_driver` map transport registers, attach hardware interrupts, negotiate VirtIO feature bits, and probe matching `virtio.h:virtio_driver` instances.
- `virtio.h:virtqueue_kick_lock` notifies the host/hypervisor via MMIO/PCI doorbell writes.

## Verification
- Run: `make test`
