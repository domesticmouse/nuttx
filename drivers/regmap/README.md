# Register Map (`regmap`) Subsystem (`drivers/regmap`)

## Overview
Provides a unified register map abstraction (`regmap`) for reading and writing peripheral device registers over I2C, SPI, or custom buses with configurable register/value bit widths, byte endianness, stride alignment, and locking.

## Interface
- `[regmap.c:regmap_init]`, `[regmap.c:regmap_exit]` - Initializes and destroys a `struct regmap_s` instance for a given `struct regmap_bus_s` and `struct regmap_config_s` (`[internal.h:struct regmap_s]`).
- `[regmap.c:regmap_read]`, `[regmap.c:regmap_write]`, `[regmap.c:regmap_bulk_read]`, `[regmap.c:regmap_bulk_write]` - Single-register and multi-register read/write operations.
- `[regmap_i2c.c:regmap_init_i2c]` - Creates a `regmap` instance backed by an I2C master bus (`[regmap_i2c.c:struct regmap_bus_i2c_s]`).
- `[regmap_spi.c:regmap_init_spi]` - Creates a `regmap` instance backed by an SPI bus (`[regmap_spi.c:struct regmap_bus_spi_s]`).

## Invariants
- Register addresses passed to read/write APIs must be multiples of `map->reg_stride` (`[regmap.c:regmap_write]`, `[regmap.c:regmap_read]`), returning `-EINVAL` otherwise.
- Unless `config->disable_locking` is set, all bus accesses are serialized via `map->lock` (`[regmap.c:regmap_lock_mutex]`).

## Side Effects
- Allocates heap memory for `struct regmap_s` and bus wrappers (`kmm_zalloc`) and executes hardware I2C (`I2C_TRANSFER`) or SPI (`SPI_EXCHANGE`, `SPI_SNDBLOCK`, `SPI_RECVBLOCK`) bus transactions.

## Verification
- Run: `make test`
