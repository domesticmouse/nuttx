# OpenBSD-Compatible Cryptographic Subsystem (`include/crypto`)

## Overview
Provides the NuttX kernel and user-space cryptographic framework (`cryptodev.h`, `cryptosoft.h`, `xform.h`) along with symmetric ciphers (AES/Rijndael, Blowfish, CAST-128, ChaCha20), cryptographic hashes and MACs (MD5, SHA-1, SHA-224/256/384/512, RIPEMD-160, SipHash, Poly1305, HMAC, AES-CMAC, AES-GMAC), key wrapping (`key_wrap.h`), asymmetric/elliptic-curve primitives (Curve25519, NIST ECC/ECDH/ECDSA, bignum `bn.h`), and randomized ID generation (`idgen.h`).

## Interface
- `cryptodev.h:cryptoini`, `cryptodev.h:cryptodesc`, `cryptodev.h:cryptop`, `cryptodev.h:cryptkop`, `cryptodev.h:session_op`, `cryptodev.h:crypt_op`, `cryptodev.h:crypto_newsession`, `cryptodev.h:crypto_freesession`, `cryptodev.h:crypto_register`, `cryptodev.h:crypto_kregister`, `cryptodev.h:crypto_unregister`, `cryptodev.h:crypto_invoke`, `cryptodev.h:crypto_kinvoke` - `/dev/crypto` session, symmetric/asymmetric operation descriptors, and hardware/software driver registration.
- `cryptosoft.h:swcr_data`, `cryptosoft.h:swcr_init`, `cryptosoft.h:swcr_process`, `xform.h:enc_xform`, `xform.h:auth_hash`, `xform.h:comp_algo`, `xform.h:authctx` - Software crypto backend and algorithm transform vtables.
- Symmetric Ciphers & AEAD: `aes.h:aes_ctx`, `aes.h:aes_setkey`, `aes.h:aes_encrypt`, `aes.h:aes_decrypt`, `rijndael.h:rijndael_set_key`, `rijndael.h:rijndael_encrypt`, `blf.h:blowfishcontext`, `blf.h:blf_key`, `blf.h:blf_ecb_encrypt`, `blf.h:blf_cbc_encrypt`, `cast.h:cast_setkey`, `cast.h:cast_encrypt`, `chachapoly.h:chacha20_ctx`, `chachapoly.h:chacha20poly1305_encrypt`, `chachapoly.h:chacha20poly1305_decrypt`, `key_wrap.h:aes_key_wrap`, `key_wrap.h:aes_key_unwrap`.
- Hashes & MACs: `md5.h:MD5_CTX`, `md5.h:md5init`, `md5.h:md5update`, `md5.h:md5final`, `sha1.h:SHA1_CTX`, `sha1.h:sha1init`, `sha1.h:sha1update`, `sha1.h:sha1final`, `sha2.h:SHA2_CTX`, `sha2.h:sha256init`, `sha2.h:sha256update`, `sha2.h:sha256final`, `sha2.h:sha512init`, `rmd160.h:RMD160_CTX`, `rmd160.h:rmd160init`, `hmac.h:hmac_sha256_init`, `hmac.h:hmac_sha256_update`, `hmac.h:hmac_sha256_final`, `cmac.h:AES_CMAC_CTX`, `cmac.h:aes_cmac_init`, `gmac.h:AES_GMAC_CTX`, `gmac.h:aes_gmac_init`, `poly1305.h:poly1305_state`, `poly1305.h:poly1305_begin`, `siphash.h:SIPHASH_CTX`, `siphash.h:siphash_init`.
- Public-Key, ECC & Bignum: `curve25519.h:curve25519`, `curve25519.h:curve25519_generate_public`, `ecc.h:ecc_make_key`, `ecc.h:ecdh_shared_secret`, `ecc.h:ecdsa_sign`, `ecc.h:ecdsa_verify`, `bn.h:bn`, `bn.h:bignum_init`, `bn.h:bignum_add`, `bn.h:bignum_mul`, `bn.h:bignum_divmod`, `idgen.h:idgen32_ctx`, `idgen.h:idgen32`.

## Invariants
- Sessions created with `cryptodev.h:crypto_newsession` must be released via `cryptodev.h:crypto_freesession` when no operations (`struct cryptop`) remain in flight.
- Key schedules and digest contexts (`aes.h:aes_ctx`, `sha2.h:SHA2_CTX`, `hmac.h:HMAC_SHA256_CTX`, `cmac.h:AES_CMAC_CTX`) must be initialized with their respective `*_init` / `*_setkey` function before calling `*_update` or `*_final`.

## Side Effects
- `cryptodev.h:crypto_register` and `cryptosoft.h:swcr_init` register cryptographic algorithm handlers in the kernel driver table (`cryptocap`) and expose `/dev/crypto` when enabled.
- `cryptodev.h:crypto_invoke` dispatches encryption/authentication requests to hardware crypto accelerators or the software fallback (`cryptosoft.h:swcr_process`), mutating caller-supplied buffers in place or in output descriptors.

## Verification
- Run: `make test`
