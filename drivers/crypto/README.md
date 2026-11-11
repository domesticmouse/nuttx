# Cryptographic and Random Number Drivers (`drivers/crypto`)

## Overview
Provides character device drivers for pseudorandom/entropy number generation (`/dev/urandom`), hardware TRNG devices (Microchip/Atmel RNG90), and the NXP SE05x Secure Element (`se05x`).

## Interface
- `dev_urandom.c:devurandom_register` - Registers the `/dev/urandom` character device backed by the kernel entropy pool (`CONFIG_DEV_URANDOM_RANDOM_POOL`), xorshift128 (`CONFIG_DEV_URANDOM_XORSHIFT128`), or linear congruential PRNG (`CONFIG_DEV_URANDOM_CONGRUENTIAL`).
- `rng90.c:rng90_register`, `rng90.c:rng90_dev_s` - Registers a character driver for the RNG90 I2C hardware random number generator.
- `se05x.c:se05x_register`, `se05x_internal.h:se05x_dev_s` - Registers a character driver for the NXP EdgeLock SE05x I2C Secure Element supporting `SE05X_IOCTL_*` commands.
- `./pnt/README.md` - NXP Plug & Trust SE05x APDU session, I2C transport, and cryptographic operation adaptation layer.

## Invariants
- `rng90.c:rng90_register` and `se05x.c:se05x_register` assert `i2c != NULL` and `devpath != NULL`.
- `dev_urandom.c:devurandom_register` PRNG inner helpers assert 4-byte buffer alignment (`((uintptr_t)buf & 3) == 0`) for word-wide PRNG writes and `len < sizeof(uint32_t)` for tail bytes.
- Only one open session is permitted at a time on `se05x` (`se05x.c:se05x_register` returns `-EBUSY` if already opened).

## Side Effects
- Registers `/dev/urandom` and hardware crypto character devices via `register_driver` (`dev_urandom.c:devurandom_register`, `rng90.c:rng90_register`, `se05x.c:se05x_register`).
- Acquires device mutexes (`nxmutex_lock`) and toggles GPIO enable pins during hardware access (`rng90.c:rng90_register`, `se05x.c:se05x_register`).
- Performs I2C transactions (`I2C_WRITE`, `I2C_READ`) and allocates device structures on the kernel heap via `kmm_malloc` (`rng90.c:rng90_register`, `se05x.c:se05x_register`).

## Verification
- Run: `make test`
