# Plug & Trust SE05x Adaptation Layer (`drivers/crypto/pnt`)

## Overview
Provides the NXP Plug & Trust (`pnt`) middleware adaptation and APDU session wrapper for the NXP EdgeLock SE05x Secure Element, including I2C transport hooks (`sm_i2c`), SCP03 platform keys, timer delays (`sm_timer`), card manager selection, and cryptographic key/data/signature operations.

## Interface
- `pnt_se05x_api.h:pnt_se05x_open`, `pnt_se05x_api.h:pnt_se05x_close`, `pnt_se05x_api.c:pnt_handle` - Opens and closes an APDU session with the SE05x secure element.
- `pnt_se05x_api.h:pnt_se05x_get_info`, `pnt_se05x_api.h:pnt_se05x_get_uid`, `pnt_util.h:select_card_manager`, `pnt_util.h:se05x_identify` - Queries applet version/OEF ID, unique module ID, and ISO7816 Card Manager status.
- `pnt_se05x_api.h:pnt_se05x_generate_keypair`, `pnt_se05x_api.h:pnt_se05x_set_public_key`, `pnt_se05x_api.h:pnt_se05x_get_key`, `pnt_se05x_api.h:pnt_se05x_delete_key`, `pnt_se05x_api.h:pnt_se05x_derive_key` - Generates, stores, retrieves, deletes, and derives (ECDH/HKDF) cryptographic keys in the secure element.
- `pnt_se05x_api.h:pnt_se05x_set_data`, `pnt_se05x_api.h:pnt_se05x_get_data`, `pnt_se05x_api.h:pnt_se05x_create_signature`, `pnt_se05x_api.h:pnt_se05x_verify_signature` - Reads/writes binary objects and performs ECDSA signature generation and verification.
- `sm_i2c.h:sm_i2c_init`, `sm_i2c.h:sm_i2c_term`, `sm_i2c.h:sm_i2c_read`, `sm_i2c.h:sm_i2c_write` - T=1 over I2C transport hooks bridging Plug & Trust to NuttX `I2C_TRANSFER`.
- `sm_timer.h:sm_sleep`, `sm_port.h:sm_malloc`, `sm_port.h:sm_free`, `scp03_keys.h:SCP03_ENC_KEY` - OS abstraction macros and SCP03 key constants.

## Invariants
- `pnt_se05x_api.c:pnt_se05x_open` requires a valid `se05x_dev_s` instance with an initialized `i2c` bus master before establishing an APDU session.
- `pnt_se05x_api.c:pnt_se05x_get_uid` requires `uid->len >= SE050_MODULE_UNIQUE_ID_LEN` (`pnt_util.h:SE050_MODULE_UNIQUE_ID_LEN`), returning `-EINVAL` otherwise.

## Side Effects
- Executes I2C bus transfers via `I2C_TRANSFER` (`sm_i2c.c:sm_i2c_read`, `sm_i2c.c:sm_i2c_write`) and sleeps the calling thread via `nxsched_usleep` (`sm_timer.c:sm_sleep`).
- Mutates persistent cryptographic objects (key pairs, binary objects) inside the external SE05x secure element (`pnt_se05x_api.c:pnt_se05x_generate_keypair`, `pnt_se05x_api.c:pnt_se05x_delete_key`).
- Allocates session handles on the kernel heap via `kmm_malloc` (`pnt_se05x_api.c:pnt_se05x_open`, `sm_port.h:sm_malloc`).

## Verification
- Run: `make test`
