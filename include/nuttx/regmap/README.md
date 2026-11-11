# NuttX Register Map Abstraction (`include/nuttx/regmap`)

## Overview
Provides a unified Register Map (`regmap`) abstraction layer over I2C, SPI, and custom hardware buses so device drivers can perform single and bulk register reads and writes without duplicating bus-specific framing and locking logic.

## Interface
- `regmap.h:regmap_bus_s`, `regmap.h:regmap_config_s` - Bus operations vtable (`reg_read`, `reg_write`, `read`, `write`) and register map configuration descriptor (`reg_bits`, `val_bits`, `reg_stride`, `disable_locking`).
- `regmap.h:regmap_init`, `regmap.h:regmap_init_i2c`, `regmap.h:regmap_init_spi`, `regmap.h:regmap_exit` - Regmap lifecycle initialization for custom buses, I2C masters (`struct i2c_master_s`), and SPI devices (`struct spi_dev_s`), plus teardown.
- `regmap.h:regmap_write`, `regmap.h:regmap_bulk_write`, `regmap.h:regmap_read`, `regmap.h:regmap_bulk_read` - Single-register and multi-register read/write accessors.

## Invariants
- `regmap.h:regmap_config_s` must specify valid bit widths (`reg_bits` and `val_bits`) supported by the underlying bus backend before calling `regmap.h:regmap_init`, `regmap.h:regmap_init_i2c`, or `regmap.h:regmap_init_spi`.
- Unless `disable_locking` is set in `regmap.h:regmap_config_s`, all `regmap_*` read/write calls serialize bus access internally and must not be invoked from contexts where sleeping on a mutex is prohibited.

## Side Effects
- `regmap.h:regmap_init`, `regmap.h:regmap_init_i2c`, and `regmap.h:regmap_init_spi` allocate heap memory for the regmap handle, freed by `regmap.h:regmap_exit`.
- `regmap.h:regmap_read`, `regmap.h:regmap_write`, `regmap.h:regmap_bulk_read`, and `regmap.h:regmap_bulk_write` perform I2C/SPI bus transactions that mutate or read peripheral hardware registers.

## Verification
- Run: `make test`
