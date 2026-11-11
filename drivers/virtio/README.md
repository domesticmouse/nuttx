# Virtio Bus, Transport, and Guest Device Drivers (`drivers/virtio`)

## Overview
Implements the NuttX Virtio guest bus framework (`virtio.c`), MMIO and PCI (legacy and modern) Virtio transports (`virtio-mmio.c`, `virtio-pci.c`, `virtio-pci-legacy.c`, `virtio-pci-modern.c`), and Virtio guest device drivers for block storage (`virtio-blk.c`), GPU framebuffer (`virtio-gpu.c`), input devices (`virtio-input.c`), network interfaces (`virtio-net.c`), random number generation (`virtio-rng.c`), Replay Protected Memory Block (`virtio-rpmb.c`), RPMSG (`virtio-rpmsg.c`), serial/console ports (`virtio-serial.c`), and sound/audio (`virtio-snd.c`).

## Interface
- `[virtio.c:virtio_register_drivers]`, `[virtio.c:virtio_register_driver]`, `[virtio.c:virtio_unregister_driver]`, `[virtio.c:virtio_register_device]`, `[virtio.c:virtio_unregister_device]`, `[virtio.c:virtio_addrenv_free_largest]`, `[virtio.c:virtio_addrenv_unmap]` - Virtio bus registration, driver-device matching, and address-environment shared-memory mapping management.
- `[virtio-mmio.c:virtio_register_mmio_device]`, `[virtio-mmio.c:virtio_register_mmio_device_secure]` - Registers a memory-mapped I/O (MMIO) Virtio transport device.
- `[virtio-pci.c:register_virtio_pci_driver]`, `[virtio-pci.c:virtio_pci_reset_device]`, `[virtio-pci.c:virtio_pci_negotiate_features]`, `[virtio-pci.c:virtio_pci_create_virtqueues]`, `[virtio-pci.c:virtio_pci_delete_virtqueues]`, `[virtio-pci-modern.c:virtio_pci_modern_probe]`, `[virtio-pci-legacy.c:virtio_pci_legacy_probe]` - Virtio PCI transport driver supporting both modern capability-based and legacy I/O BAR devices.
- Guest driver registration functions:
  - `[virtio-blk.c:virtio_register_blk_driver]` - Virtio block driver (`/dev/virtblkN`).
  - `[virtio-gpu.c:virtio_register_gpu_driver]`, `[virtio-gpu.c:virtio_gpu_fb_register]` - Virtio 2D GPU framebuffer driver.
  - `[virtio-input.c:virtio_register_input_driver]` - Virtio keyboard/mouse/touch input driver.
  - `[virtio-net.c:virtio_register_net_driver]` - Virtio network interface driver.
  - `[virtio-rng.c:virtio_register_rng_driver]` - Virtio `/dev/urandom` entropy source driver.
  - `[virtio-rpmb.c:virtio_register_rpmb_driver]` - Virtio `/dev/rpmb` character driver.
  - `[virtio-rpmsg.c:virtio_register_rpmsg_driver]` - Virtio RPMSG transport driver.
  - `[virtio-serial.c:virtio_register_serial_driver]` - Virtio `/dev/ttyV*` serial/console driver.
  - `[virtio-snd.c:virtio_register_snd_driver]` - Virtio `/dev/audio/pcm*` audio driver.

## Invariants
- `[virtio.c:virtio_register_driver]` asserts `DEBUGASSERT(driver != NULL && driver->probe != NULL && driver->remove != NULL)`.
- `[virtio-mmio.c:virtio_register_mmio_device]` asserts `DEBUGASSERT(regs != NULL)` and verifies `VIRTIO_MMIO_MAGIC_VALUE` (`0x74726976`) and supported MMIO version (`1` or `2`).
- `[virtio-snd.c:virtio_register_snd_driver]` audio callbacks assert `DEBUGASSERT(caps->ac_len >= sizeof(struct audio_caps_s))` and `DEBUGASSERT(desc->u.pbuffer != NULL)`.

## Side Effects
- Negotiates Virtio feature bits, allocates DMA/shared-memory virtqueues (`virtio_create_virtqueues`), and attaches MMIO or PCI MSI-X/legacy interrupts.
- Registers block devices (`register_blockdriver`), character devices (`register_driver`), network devices (`netdev_register`), framebuffer devices, input devices, and audio devices (`audio_register`).
- Enqueues scatter-gather buffers (`virtqueue_add_buffer`) and notifies hypervisor/host backends (`virtqueue_kick`) under `spin_lock_irqsave`.

## Verification
- Run: `make test`
