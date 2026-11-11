# Power Relay Drivers (`drivers/power/relay`)

## Overview
Implements the upper-half relay character driver (`/dev/relayN`) and the GPIO-backed relay lower-half driver.

## Interface
- `[relay.c:relay_register]` - Registers a relay character device supporting `RELAYIOC_SET` and `RELAYIOC_GET` ioctls (`[relay.c:g_relay_ops]`).
- `[relay_gpio.c:relay_gpio_register]` - Registers a GPIO-controlled relay device using an `ioexpander_dev_s` instance (`[relay_gpio.c:struct relay_gpio_priv]`).

## Invariants
- `[relay.c:relay_ioctl]` asserts `inode->i_private != NULL` and non-null ioctl argument pointers (`DEBUGASSERT`) and serializes access via `dev->lock` (`[relay.c:nxmutex_lock]`).

## Side Effects
- Registers VFS character devices (`[relay.c:register_driver]`) and toggles physical GPIO/IO-expander output pins via `IOEXP_WRITEPIN` / `IOEXP_READPIN`.

## Verification
- Run: `make test`
