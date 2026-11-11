# Bluetooth HCI and Transport Drivers (`drivers/wireless/bluetooth`)

## Overview
Implements NuttX Bluetooth Host Controller Interface (HCI) registration (`bt_driver.c`), dual-stack Classic/BLE HCI multiplexing bridge (`bt_bridge.c`), SLIP H5 3-wire framing (`bt_slip.c`), cross-core RPMSG HCI transport (`bt_rpmsghci.c`, `bt_rpmsghci_server.c`), null test driver (`bt_null.c`), and UART H4 lower-half/upper-half drivers (`bt_uart.c`, `bt_uart_generic.c`, `bt_uart_bcm4343x.c`, `bt_uart_cc2564.c`, `bt_uart_shim.c`).

## Interface
- `[bt_driver.c:bt_driver_register]`, `[bt_driver.c:bt_driver_register_with_id]` - Registers a `struct bt_driver_s` HCI controller with the configured Bluetooth stack (`bt_netdev_register`), optionally wrapping it in H5 SLIP, HCI Bridge, and/or BTH4 character device layers.
- `[bt_bridge.c:bt_bridge_register]` - Splits a single physical Bluetooth HCI driver into separate Classic BT and BLE virtual `bt_driver_s` instances with opcode/event filtering.
- `[bt_slip.c:bt_slip_register]` - Wraps a `bt_driver_s` with Bluetooth Three-Wire UART (H5) SLIP framing, sequence numbering, and retransmission.
- `[bt_rpmsghci.c:rpmsghci_register]`, `[bt_rpmsghci_server.c:rpmshci_server_init]`, `[bt_rpmsghci_server.c:rpmsghci_bt_receive]` - Client and server drivers for tunneling Bluetooth HCI commands, ACL/SCO data, and events across cores over RPMSG.
- `[bt_null.c:btnull_register]` - Registers a stub Bluetooth HCI driver for testing.
- `[bt_uart.c:btuart_register]`, `[bt_uart.c:btuart_open]`, `[bt_uart.c:btuart_close]`, `[bt_uart.c:btuart_send]`, `[bt_uart.c:btuart_ioctl]` - Core H4 UART upper-half HCI operations.
- `[bt_uart_generic.c:btuart_create]`, `[bt_uart_bcm4343x.c:btuart_create]`, `[bt_uart_cc2564.c:btuart_create]`, `[bt_uart_cc2564.c:load_cc2564_firmware]` - Instantiates generic, Broadcom BCM4343x, or TI CC2564 H4 UART Bluetooth drivers (including firmware patch loading).
- `[bt_uart_shim.c:btuart_shim_getdevice]` - Adapts a standard VFS serial character device (`/dev/ttyS*`) into a `struct btuart_lowerhalf_s` interface.

## Invariants
- `[bt_uart.c:btuart_open]`, `[bt_uart.c:btuart_send]`, and `[bt_uart.c:btuart_ioctl]` assert `DEBUGASSERT(upper != NULL && upper->lower != NULL)` and `DEBUGASSERT(lower->read != NULL)`.
- `[bt_rpmsghci.c:rpmsghci_register]` and `[bt_slip.c:bt_slip_register]` callbacks assert non-null `btdev`/`dev` pointers.

## Side Effects
- Registers Bluetooth network interfaces (`netdev_register` via `bt_netdev_register`) or `/dev/ttyBT*` character devices (`uart_bth4_register`).
- Opens serial devices (`file_open` in `bt_uart_shim.c`), uploads vendor firmware blobs over HCI UART (`bt_uart_bcm4343x.c`, `bt_uart_cc2564.c`), schedules RX/retransmission work on `HPWORK`/`LPWORK`, and exchanges cross-core RPMSG packets (`rpmsg_send_nocopy`).

## Verification
- Run: `make test`
