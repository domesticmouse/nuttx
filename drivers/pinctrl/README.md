# Pin Control Upper-Half Driver (`drivers/pinctrl`)

## Overview
Implements the upper-half Pin Control (`pinctrl`) character driver (`/dev/pinctrlN`) and optional `/proc/pinctrl` diagnostic interface for configuring SoC pin multiplexing, drive strength, slew rate, and bias settings.

## Interface
- `[pinctrl.c:pinctrl_register]` - Registers a pin controller character device (`/dev/pinctrl<minor>`) and optional procfs node for a `struct pinctrl_dev_s` instance (`[pinctrl.c:struct pinctrl_entry_s]`).
- `[pinctrl.c:pinctrl_unregister]` - Unregisters `/dev/pinctrl<minor>` and removes the controller from the procfs tracking list (`[pinctrl.c:CONFIG_PINCTRL_PROCFS]`).

## Invariants
- `[pinctrl.c:pinctrl_ioctl]` requires `dev->ops` to be non-null (`DEBUGASSERT(dev->ops != NULL)`) and protects procfs controller list mutations with `[pinctrl.c:g_pinctrl_lock]` (`nxmutex_lock`).

## Side Effects
- Registers and unregisters VFS character devices (`[pinctrl.c:register_driver]`, `unregister_driver`) and `/proc/pinctrl` procfs entries (`procfs_register`), and mutates hardware pinmux/pad configuration registers via lower-half `ops` callbacks.

## Verification
- Run: `make test`
