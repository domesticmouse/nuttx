# Cryptographic & Secure Element Headers (`include/nuttx/crypto`)

## Overview
Defines kernel cryptographic primitives, hardware crypto initialization, symmetric ciphers (AES, TEA), cryptographic hashing (BLAKE2s), and character driver interfaces for hardware random number generators (RNG90) and secure elements (NXP EdgeLock SE05x).

## Interface
- `crypto.h:up_cryptoinitialize`, `crypto.h:aes_cypher`, `crypto.h:crypto_test`, `crypto.h:AES_MODE_ECB`, `crypto.h:AES_MODE_CBC`, `crypto.h:AES_MODE_CTR`, `crypto.h:AES_MODE_CFB`, `crypto.h:CYPHER_ENCRYPT`, `crypto.h:CYPHER_DECRYPT` - Architecture crypto initialization, AES cipher interface, and algorithm self-test entry point.
- `blake2s.h:blake2s_state`, `blake2s.h:blake2s_param`, `blake2s.h:blake2s_init`, `blake2s.h:blake2s_init_key`, `blake2s.h:blake2s_init_param`, `blake2s.h:blake2s_update`, `blake2s.h:blake2s_final`, `blake2s.h:blake2s` - BLAKE2s cryptographic hash function state and streaming/one-shot APIs.
- `tea.h:tea_encrypt`, `tea.h:tea_decrypt` - Tiny Encryption Algorithm (TEA) 64-bit block cipher routines.
- `rng90.h:rng90_register`, `rng90.h:RNG90_IOC_WAKEUP`, `rng90.h:RNG90_IOC_SLEEP`, `rng90.h:RNG90_IOC_GENRND` - Atmel/Microchip RNG90 I2C hardware random number generator driver and `ioctl` commands.
- `se05x.h:se05x_config_s`, `se05x.h:se05x_register`, `se05x.h:SEIOC_GET_INFO`, `se05x.h:SEIOC_GET_UID`, `se05x.h:SEIOC_GENERATE_KEYPAIR`, `se05x.h:SEIOC_SET_KEY`, `se05x.h:SEIOC_GET_KEY`, `se05x.h:SEIOC_CREATE_SIGNATURE`, `se05x.h:SEIOC_VERIFY_SIGNATURE`, `se05x.h:SEIOC_DERIVE_SYMM_KEY` - NXP SE05x I2C secure element driver, key store/signature structures, and `ioctl` commands.

## Invariants
- `blake2s.h:blake2s_constant` constrains BLAKE2s block size to `BLAKE2S_BLOCKBYTES` (`64`), maximum digest length to `BLAKE2S_OUTBYTES` (`32`), and maximum key length to `BLAKE2S_KEYBYTES` (`32`).
- `tea.h:tea_encrypt` and `tea.h:tea_decrypt` require a 2-word (`uint32_t[2]`) value buffer and a 4-word (`uint32_t[4]`) 128-bit key buffer.

## Side Effects
- `crypto.h:up_cryptoinitialize` initializes hardware cryptographic engines.
- `rng90.h:rng90_register` and `se05x.h:se05x_register` register character devices in the VFS and communicate with external security ICs over I2C (including persistent key generation/deletion in SE05x non-volatile memory).

## Verification
- Run: `make test`
