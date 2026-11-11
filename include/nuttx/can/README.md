# CAN Bus Subsystem Headers (`include/nuttx/can`)

## Overview
Defines the NuttX Controller Area Network (CAN and CAN-FD) character driver framework, transmit priority queue/FIFO caching (`can_sender.h`), ISO-TP (ISO 15765-2) transport protocol framing, and lower-half controller drivers (MCP2515, SJA1000, CTU CAN FD PCI, Kvaser PCI).

## Interface
- `can.h:can_dev_s`, `can.h:can_ops_s`, `can.h:can_msg_s`, `can.h:can_hdr_s`, `can.h:can_rtrread_s` - Core CAN character driver structures, lower-half vtable, and message frame formats.
- `can.h:can_register`, `can.h:can_receive`, `can.h:can_txdone`, `can.h:can_txready` - Upper-half CAN registration and interrupt-level receive/transmit-complete notification functions.
- `can.h:CANIOC_RTR`, `can.h:CANIOC_GET_BITTIMING`, `can.h:CANIOC_SET_BITTIMING`, `can.h:CANIOC_ADD_STDFILTER`, `can.h:CANIOC_ADD_EXTFILTER`, `can.h:CANIOC_SET_CONNMODES`, `can.h:CANIOC_BUSOFF_RECOVERY`, `can.h:CANIOC_IFLUSH`, `can.h:CANIOC_OFLUSH` - CAN controller `ioctl` commands.
- `can_common.h:can_bytes2dlc`, `can_common.h:can_dlc2bytes` - CAN/CAN-FD payload length to Data Length Code (DLC) conversion helpers.
- `can_sender.h:can_sender_init`, `can_sender.h:can_add_sendnode`, `can_sender.h:can_get_msg`, `can_sender.h:can_revert_msg`, `can_sender.h:can_send_done`, `can_sender.h:can_txneed_cancel`, `can_sender.h:can_cancel_mbmsg` - CAN TX cache queue management (ring-buffer or strict priority list when `CONFIG_CAN_STRICT_TX_PRIORITY` is set).
- `isotp.h:can_isotp_options`, `isotp.h:can_isotp_ll_options`, `isotp.h:can_isotp_fc_options`, `isotp.h:isotp_encode_s`, `isotp.h:isotp_encode_init`, `isotp.h:isotp_encode_frame`, `isotp.h:isotp_decode_init`, `isotp.h:isotp_decode_frame`, `isotp.h:isotp_build_fc` - ISO 15765-2 (ISO-TP) single/first/consecutive/flow-control frame encoding and decoding.
- `ctucanfd_pci.h:pci_ctucanfd_init`, `kvaser_pci.h:pci_kvaser_init`, `mcp2515.h:mcp2515_instantiate`, `mcp2515.h:mcp2515_initialize`, `sja1000.h:sja1000_instantiate` - Hardware CAN controller initialization APIs.

## Invariants
- `can.h:CONFIG_CAN_TXFIFOSIZE`, `can.h:CONFIG_CAN_RXFIFOSIZE`, and `can.h:CONFIG_CAN_NPENDINGRTR` are clamped to a maximum of `255`.
- `can.h:CAN_MAXDATALEN` is `64` when `CONFIG_CAN_FD` is enabled and `8` otherwise.
- `isotp.h:isotp_encode_init` rejects payloads exceeding `ISOTP_MAX_MSG_LEN` (`4095`) with `-EMSGSIZE` unless `CONFIG_LIBC_CAN_ISOTP_LONG_PDU` is enabled.

## Side Effects
- `can.h:can_register` allocates upper-half state and registers a CAN character device in the VFS.
- `can.h:can_receive` and `can.h:can_txdone` mutate RX/TX software queues and post semaphores or workqueue jobs to wake waiting threads.
- `sja1000.h:sja1000_putreg` and `sja1000.h:sja1000_modifyreg32` directly mutate hardware controller registers.

## Verification
- Run: `make test`
