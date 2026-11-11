# I2S Character Driver (`drivers/i2s`)

## Overview
Implements a generic character device wrapper (`/dev/i2scharN`) around a lower-half `i2s_dev_s` instance, allowing userspace applications and test utilities to stream raw `ap_buffer_s` audio buffers over an I2S bus via standard `read` and `write` system calls.

## Interface
- `i2schar.c:i2schar_register` - Allocates an `i2schar.c:i2schar_dev_s` instance and registers an I2S character device at `/dev/i2schar[minor]`.
- `i2schar.c:i2schar_dev_s` - Character driver state structure holding the underlying `i2s_dev_s` pointer, mutex (`exclsem`), and minor number.

## Invariants
- `i2schar.c:i2schar_register` asserts `i2s != NULL` and `(unsigned)minor < 100`.
- `i2schar_read` and `i2schar_write` assert `buflen >= (sizeof(struct ap_buffer_s) + CONFIG_DRIVERS_AUDIO_BUFSIZE)` so that each read/write call transfers a complete `ap_buffer_s` header and payload (`i2schar.c:i2schar_register`).

## Side Effects
- Acquires `priv->exclsem` via `nxmutex_lock` and blocks on buffer completion semaphores via `nxsem_wait` (`i2schar.c:i2schar_register`).
- Invokes lower-half `I2S_RECEIVE`, `I2S_SEND`, and `I2S_IOCTL` methods to initiate DMA/interrupt I2S transfers (`i2schar.c:i2schar_register`).
- Allocates `i2schar.c:i2schar_dev_s` via `kmm_zalloc` and registers `/dev/i2scharN` via `register_driver` (`i2schar.c:i2schar_register`).

## Verification
- Run: `make test`
