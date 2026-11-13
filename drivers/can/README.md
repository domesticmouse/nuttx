# CAN Character Drivers (`drivers/can`)

## Overview
Implements the NuttX Controller Area Network (CAN) upper-half character driver, priority-ordered TX queue/mailbox management, DLC-to-byte conversion utilities, and lower-half controller drivers for MCP2515 (SPI), SJA1000, Kvaser PCI, and CTU CAN FD PCI devices.

## Interface
- `can.c:can_register` - Registers a CAN character device node wrapping a `can_dev_s` lower-half instance.
- `can.c:can_receive`, `can.c:can_txdone`, `can.c:can_txready` - Upper-half callbacks invoked by lower-half interrupt handlers to enqueue received CAN frames and advance TX state.
- `can_sender.c:can_sender_init`, `can_sender.c:can_add_sendnode`, `can_sender.c:can_get_msg`, `can_sender.c:can_revert_msg`, `can_sender.c:can_send_done`, `can_sender.c:can_txneed_cancel`, `can_sender.c:can_cancel_mbmsg` - Manages TX FIFO/priority queues (`tx_pendq`, `tx_sendingq`, `tx_freeq`) and hardware mailbox cancellation.
- `mcp2515.c:mcp2515_instantiate`, `mcp2515.c:mcp2515_initialize`, `mcp2515.c:mcp2515_can_s` - Instantiates and binds the Microchip MCP2515 SPI CAN controller.
- `sja1000.c:sja1000_instantiate`, `kvaser_pci.c:pci_kvaser_init`, `ctucanfd_pci.c:pci_ctucanfd_init`, `ctucanfd.h:ctucanfd_frame_s` - Initializes SJA1000, Kvaser PCI, and CTU CAN FD PCI CAN controllers.

## Invariants
- `can.c:can_register` requires a non-null `dev` pointer and initializes `cd_Senders` (`can_sender.c:can_sender_init`) before exposing the device node.
- Reader/writer list manipulation and TX/RX queue state transitions must execute inside a critical section (`enter_critical_section`) or spinlock (`sja1000.c:sja1000_instantiate`).
- `mcp2515.c:mcp2515_instantiate` requires a valid `mcp2515_config_s` and SPI device handle.

## Side Effects
- Registers and unregisters VFS character drivers via `register_driver` and `unregister_driver` (`can.c:can_register`, `ctucanfd_pci.c:pci_ctucanfd_init`, `kvaser_pci.c:pci_kvaser_init`).
- Performs SPI transfers (`SPI_SEND`, `SPI_EXCHANGE` in `mcp2515.c:mcp2515_initialize`), PCI BAR mapping and IRQ attachment (`ctucanfd_pci.c:pci_ctucanfd_init`, `kvaser_pci.c:pci_kvaser_init`), and schedules work queues (`work_queue` in `can.c:can_txdone`).
- Signals waiting readers, writers, and `poll` descriptors via `nxsem_post` and `poll_notify` (`can.c:can_receive`, `can.c:can_txdone`).

## Verification
- Run: `make test`
