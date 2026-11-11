# USB Type-C and Power Delivery Miscellaneous Drivers (`drivers/usbmisc`)

## Overview
Provides I2C character drivers for USB Type-C port controllers and USB Power Delivery (USB-PD) controller ICs, including the ON Semiconductor FUSB301 (`fusb301.c`), FUSB302 (`fusb302.c`), FUSB303 (`fusb303.c`), and STMicroelectronics STUSB4500 (`stusb4500.c`).

## Interface
- `[fusb301.c:fusb301_register]` - Registers an ON Semiconductor FUSB301 USB Type-C controller character device and attaches its hardware interrupt handler.
- `[fusb302.c:fusb302_register]` - Registers an ON Semiconductor FUSB302 programmable USB Type-C / PD controller character device.
- `[fusb303.c:fusb303_register]` - Registers an ON Semiconductor FUSB303 autonomous USB Type-C port controller character device.
- `[stusb4500.c:stusb4500_register]` - Registers an STMicroelectronics STUSB4500 standalone USB Power Delivery sink controller character device.

## Invariants
- `[fusb301.c:fusb301_register]`, `[fusb302.c:fusb302_register]`, and `[fusb303.c:fusb303_register]` require non-null configuration and I2C bus pointers (`DEBUGASSERT(config != NULL)`, `DEBUGASSERT(i2c != NULL)`).
- `[stusb4500.c:stusb4500_register]` asserts `DEBUGASSERT(devpath != NULL && i2c != NULL)`.
- File operations (`open`, `close`, `read`, `ioctl`, `poll`) assert `DEBUGASSERT(inode->i_private)` and `DEBUGASSERT(priv)`.

## Side Effects
- Registers character devices (e.g., `/dev/fusb301`, `/dev/fusb302`, `/dev/fusb303`, `/dev/stusb4500`) via `register_driver`.
- Performs I2C register reads and writes (`I2C_TRANSFER`) to configure CC pin pull-up/pull-down resistors, VCONN switches, current limits, and PDO profiles.
- Attaches GPIO interrupt handlers via lower-half `irq_attach`/`irq_enable` callbacks, wakes poll waiters (`poll_notify`), and serializes device state using `nxmutex_lock` and critical sections (`enter_critical_section`).

## Verification
- Run: `make test`
