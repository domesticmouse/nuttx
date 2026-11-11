# Modem Drivers (`drivers/modem`)

## Overview
Provides upper-half character drivers and protocol stacks for cellular modems in NuttX, including u-blox cellular modems and the Sony Altair ALT1250 LTE modem subsystem.

## Interface
- `[u-blox.c:ubxmdm_register]` - Registers a u-blox modem character device bound to a `struct ubxmdm_lower` lower-half instance (`[u-blox.c:struct ubxmdm_upper]`).
- `[u-blox.c:ubxmdm_unregister]` - Unregisters a u-blox modem character device and frees upper-half state.
- Subdirectories:
  - [./alt1250/README.md](./alt1250/README.md) - Sony Altair ALT1250 LTE-M/NB-IoT modem driver, SPI transport, and ALTCOM protocol handlers.

## Invariants
- `[u-blox.c:ubxmdm_register]` requires non-null `path`, `lower`, and `lower->ops` pointers (`DEBUGASSERT`).

## Side Effects
- Registers and unregisters VFS character device nodes (`[u-blox.c:register_driver]`, `unregister_driver`) and delegates modem power/reset/status ioctls to lower-half hardware callbacks.

## Verification
- Run: `make test`
