# NuttX Bluetooth & BLE Subsystem (`include/nuttx/wireless/bluetooth`)

## Overview
Provides the NuttX Bluetooth / Bluetooth Low Energy (`BLE`) core protocol definitions (`bt_core.h`), Host Controller Interface (`bt_hci.h`), Generic Attribute Profile (`bt_gatt.h`), UUID manipulation (`bt_uuid.h`), reference-counted packet buffers (`bt_buf.h`), network/socket `ioctl` commands (`bt_ioctl.h`), lower-half HCI driver abstraction (`bt_driver.h`), and transport drivers (H4 UART, SLIP/H5, RPMsg HCI, H4 bridge, and null test driver).

## Interface
- `bt_core.h:bt_eir_s`, `bt_core.h:bt_security_e`, `bt_core.h:bt_addr_to_str`, `bt_core.h:bt_add_services`, `bt_uuid.h:bt_uuid_s`, `bt_uuid.h:bt_uuid_type_e`, `bt_uuid.h:bt_uuid_cmp` - Core address formatting, Extended Inquiry Response (`EIR`), security levels, and 16/32/128-bit UUID representation.
- `bt_hci.h:bt_addr_s`, `bt_hci.h:bt_addr_le_s`, `bt_hci.h:bt_hci_cmd_hdr_s`, `bt_hci.h:bt_hci_evt_hdr_s`, `bt_hci.h:bt_hci_acl_hdr_s`, `bt_hci.h:bt_hci_iso_hdr_s` - Bluetooth device addresses and HCI command, event, ACL, and ISO packet wire headers and opcodes.
- `bt_buf.h:bt_buf_s`, `bt_buf.h:bt_buf_type_e`, `bt_buf.h:bt_buf_alloc`, `bt_buf.h:bt_buf_release`, `bt_buf.h:bt_buf_addref`, `bt_buf.h:bt_buf_extend`, `bt_buf.h:bt_buf_provide`, `bt_buf.h:bt_buf_consume` - Reference-counted Bluetooth frame buffer allocation and cursor manipulation.
- `bt_gatt.h:bt_gatt_attr_s`, `bt_gatt.h:bt_gatt_service_s`, `bt_gatt.h:bt_gatt_chrc_s`, `bt_gatt.h:bt_gatt_ccc_s`, `bt_gatt.h:bt_gatt_register`, `bt_gatt.h:bt_gatt_notify`, `bt_gatt.h:bt_gatt_discover`, `bt_gatt.h:bt_gatt_exchange_mtu` - BLE GATT attribute table registration, server notifications, and client discovery APIs.
- `bt_driver.h:bt_driver_s`, `bt_driver.h:bt_driver_register`, `bt_driver.h:bt_driver_register_with_id`, `bt_driver.h:bt_netdev_register`, `bt_driver.h:bt_netdev_unregister`, `bt_driver.h:bt_netdev_receive` - HCI controller driver interface (`open`, `send`, `close`, `receive`, `ioctl`) and network stack registration.
- `bt_ioctl.h:btreq_s`, `bt_ioctl.h:bt_scanresponse_s`, `bt_ioctl.h:bt_discresonse_s`, `bt_ioctl.h:SIOCGBTINFO`, `bt_ioctl.h:SIOCBTADVSTART`, `bt_ioctl.h:SIOCBTSCANSTART`, `bt_ioctl.h:SIOCBTCONNECT` - `bthci*` network interface `ioctl` commands and request structures.
- HCI Transports: `bt_uart.h:btuart_lowerhalf_s`, `bt_uart.h:btuart_register`, `bt_uart_shim.h:btuart_shim_getdevice`, `bt_slip.h:bt_slip_register`, `bt_rpmsghci.h:rpmsghci_register`, `bt_rpmsghci.h:rpmshci_server_init`, `bt_bridge.h:bt_bridge_register`, `bt_null.h:btnull_register`.

## Invariants
- Every `bt_driver.h:bt_driver_s` implementation must set `head_reserve` to the byte count required by its transport header (e.g., `H4_HEADER_SIZE` in `bt_uart.h`) so `bt_buf.h:bt_buf_alloc` reserves sufficient headroom before the HCI payload.
- All `bt_hci.h` protocol structures are packed (`begin_packed_struct`) and use little-endian byte order (`BT_HOST2LE16` / `BT_LE162HOST`).

## Side Effects
- `bt_driver.h:bt_driver_register` (and `bt_driver.h:bt_netdev_register`) initializes the Bluetooth stack or HCI socket adapter and registers a `bthciN` network device.
- `bt_gatt.h:bt_gatt_register` appends GATT service attribute descriptors to the global BLE attribute database.

## Verification
- Run: `make test`
