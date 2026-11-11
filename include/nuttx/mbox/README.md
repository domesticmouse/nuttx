# Mailbox (IPC) Subsystem Headers (`include/nuttx/mbox`)

## Overview
Defines the generic NuttX inter-processor Mailbox (`mbox`) driver abstraction for sending notifications/messages and registering receive callbacks across hardware mailbox channels.

## Interface
- `mbox.h:mbox_dev_s`, `mbox.h:mbox_ops_s`, `mbox.h:mbox_receive_t` - Mailbox device structure, lower-half operation vtable (`send`, `registercallback`), and channel receive callback signature.
- `mbox.h:MBOX_SEND`, `mbox.h:MBOX_REGISTER_CALLBACK`, `mbox.h:MBOX_UNREGISTER_CALLBACK` - Dispatch macros for transmitting messages on a channel and attaching/detaching receive callbacks.

## Invariants
- `mbox.h:mbox_dev_s.ops` (`mbox_ops_s`) must be non-null and provide valid `send` and `registercallback` pointers before invoking `MBOX_SEND`, `MBOX_REGISTER_CALLBACK`, or `MBOX_UNREGISTER_CALLBACK`.

## Side Effects
- `mbox.h:MBOX_SEND` writes to hardware mailbox registers and triggers an inter-processor interrupt (IPI) on the remote core/channel.
- `mbox.h:MBOX_REGISTER_CALLBACK` and `mbox.h:MBOX_UNREGISTER_CALLBACK` mutate the driver's per-channel interrupt callback state.

## Verification
- Run: `make test`
