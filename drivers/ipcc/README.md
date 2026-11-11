# Inter-Processor Communication Controller (IPCC) Driver (`drivers/ipcc`)

## Overview
Implements the upper-half character driver (`/dev/ipccN`) for Inter-Processor Communication Controller (IPCC) channels, providing buffered or unbuffered cross-core message streaming, blocking/non-blocking `read` and `write`, `poll` notifications, and pseudofs `unlink` cleanup over an `ipcc_lower_s` hardware lower half.

## Interface
- `ipcc_register.c:ipcc_register`, `ipcc_register.c:ipcc_cleanup` - Allocates an `ipcc_priv.h:ipcc_driver_s` instance, initializes optional RX/TX circular buffers (`CONFIG_IPCC_BUFFERED`), and registers `/dev/ipcc<chan>`.
- `ipcc_open.c:ipcc_open`, `ipcc_close.c:ipcc_close`, `ipcc_unlink.c:ipcc_unlink` - Manages open reference counts (`crefs`) and defers final `ipcc_cleanup` if the device is unlinked while open.
- `ipcc_read.c:ipcc_read`, `ipcc_read.c:ipcc_rxfree_notify` - Reads incoming data from the IPCC channel or RX `circbuf_s` and notifies the lower half when buffer space is freed.
- `ipcc_write.c:ipcc_write`, `ipcc_write.c:ipcc_txfree_notify` - Writes outgoing data to the IPCC channel or TX `circbuf_s` and wakes blocked writers when TX space becomes available.
- `ipcc_poll.c:ipcc_poll`, `ipcc_priv.h:ipcc_pollnotify` - Implements `poll` setup/teardown and dispatches `POLLIN`/`POLLOUT` events.

## Invariants
- `ipcc_register.c:ipcc_register` requires a valid `ipcc_lower_s` pointer (`ipcc != NULL`) and initializes `crefs = 0` and `unlinked = 0`.
- `ipcc_register.c:ipcc_cleanup` must only be called when `crefs <= 0` and `unlinked == 1` (`ipcc_close.c:ipcc_close`, `ipcc_unlink.c:ipcc_unlink`).
- Access to circular buffers (`rxbuf`, `txbuf`) and lower-half TX/RX state is synchronized under `priv->lock` (`nxmutex_lock`) and critical sections (`enter_critical_section`).

## Side Effects
- Acquires `priv->lock` via `nxmutex_lock`, blocks threads on `priv->rxsem` and `priv->txsem` via `nxsem_wait`, and enters critical sections (`enter_critical_section`) (`ipcc_read.c:ipcc_read`, `ipcc_write.c:ipcc_write`).
- Invokes lower-half `ipcc->ops` callbacks (`read`, `write`, `bufinit`, `rxfree`, `txenable`, `cleanup`) to interact with hardware IPCC mailboxes (`ipcc_read.c:ipcc_read`, `ipcc_write.c:ipcc_write`, `ipcc_register.c:ipcc_cleanup`).
- Allocates driver state and circular buffers on the kernel heap (`kmm_zalloc`, `circbuf_init`), registers `/dev/ipccN` via `register_driver`, and notifies poll waiters via `poll_notify` (`ipcc_register.c:ipcc_register`, `ipcc_poll.c:ipcc_poll`).

## Verification
- Run: `make test`
