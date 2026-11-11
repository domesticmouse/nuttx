# MIPI DSI Host and Device Subsystem (`drivers/video/mipidsi`)

## Overview
Implements the MIPI Display Serial Interface (DSI) bus abstraction for NuttX, including DSI packet framing (`mipi_dsi_packet.c`), DSI host controller registration and character device exposure (`mipi_dsi_host.c`, `mipi_dsi_host_driver.c`), and DSI peripheral device attachment, DCS/generic command helpers, and character device exposure (`mipi_dsi_device.c`, `mipi_dsi_device_driver.c`).

## Interface
- `[mipi_dsi_host.c:mipi_dsi_host_register]`, `[mipi_dsi_host.c:mipi_dsi_host_unregister]`, `[mipi_dsi_host.c:mipi_dsi_host_get]` - Registers, unregisters, and looks up a `struct mipi_dsi_host` instance by bus number.
- `[mipi_dsi_host_driver.c:mipi_dsi_host_driver_register]` - Exposes a MIPI DSI host controller as `/dev/dsiN` in the VFS.
- `[mipi_dsi_device.c:mipi_dsi_device_register]`, `[mipi_dsi_device.c:mipi_dsi_attach]`, `[mipi_dsi_device.c:mipi_dsi_detach]`, `[mipi_dsi_device.c:mipi_dsi_transfer]` - Creates a `struct mipi_dsi_device` on a DSI host and executes DSI message transfers.
- `[mipi_dsi_device.c:mipi_dsi_dcs_write]`, `[mipi_dsi_device.c:mipi_dsi_dcs_write_buffer]`, `[mipi_dsi_device.c:mipi_dsi_dcs_read]`, `[mipi_dsi_device.c:mipi_dsi_generic_write]`, `[mipi_dsi_device.c:mipi_dsi_generic_read]`, `[mipi_dsi_device.c:mipi_dsi_shutdown_peripheral]`, `[mipi_dsi_device.c:mipi_dsi_turn_on_peripheral]`, `[mipi_dsi_device.c:mipi_dsi_set_maximum_return_packet_size]`, `[mipi_dsi_device.c:mipi_dsi_compression_mode]`, `[mipi_dsi_device.c:mipi_dsi_picture_parameter_set]`, `[mipi_dsi_device.c:mipi_dsi_dcs_nop]`, `[mipi_dsi_device.c:mipi_dsi_dcs_soft_reset]`, `[mipi_dsi_device.c:mipi_dsi_dcs_enter_sleep_mode]`, `[mipi_dsi_device.c:mipi_dsi_dcs_exit_sleep_mode]`, `[mipi_dsi_device.c:mipi_dsi_dcs_set_display_off]`, `[mipi_dsi_device.c:mipi_dsi_dcs_set_display_on]`, `[mipi_dsi_device.c:mipi_dsi_dcs_set_column_address]`, `[mipi_dsi_device.c:mipi_dsi_dcs_set_page_address]`, `[mipi_dsi_device.c:mipi_dsi_dcs_set_tear_off]`, `[mipi_dsi_device.c:mipi_dsi_dcs_set_tear_on]`, `[mipi_dsi_device.c:mipi_dsi_dcs_set_pixel_format]`, `[mipi_dsi_device.c:mipi_dsi_dcs_set_tear_scanline]`, `[mipi_dsi_device.c:mipi_dsi_dcs_set_display_brightness]`, `[mipi_dsi_device.c:mipi_dsi_dcs_get_display_brightness]` - Standard MIPI DCS and generic packet command helpers.
- `[mipi_dsi_device_driver.c:mipi_dsi_device_driver_register]` - Registers a VFS character device (`/dev/dsiN/dev-*`) for a MIPI DSI peripheral.
- `[mipi_dsi_packet.c:mipi_dsi_create_packet]`, `[mipi_dsi_packet.c:mipi_dsi_packet_format_is_short]`, `[mipi_dsi_packet.c:mipi_dsi_packet_format_is_long]`, `[mipi_dsi_packet.c:mipi_dsi_pixel_format_to_bpp]` - Formats short and long MIPI DSI packets and maps pixel format enums to bits-per-pixel.

## Invariants
- `[mipi_dsi_host.c:mipi_dsi_host_register]` asserts `DEBUGASSERT(host != NULL && host->ops != NULL)`.
- `[mipi_dsi_device.c:mipi_dsi_device_register]` asserts `DEBUGASSERT(host != NULL && name != NULL)` and rejects virtual channels `channel > 3`.
- `[mipi_dsi_packet.c:mipi_dsi_create_packet]` asserts `DEBUGASSERT(packet != NULL)` and `DEBUGASSERT(msg != NULL)`.

## Side Effects
- `[mipi_dsi_host.c:mipi_dsi_host_register]` appends the host to the global `g_dsi_hosts` list under `nxmutex_lock` and optionally creates `/dev/dsiN` via `register_driver`.
- `[mipi_dsi_device.c:mipi_dsi_transfer]` invokes `device->host->ops->transfer` to transmit DSI packets over the physical D-PHY link.

## Verification
- Run: `make test`
