# LZF Compression and Decompression (`libs/libc/lzf`)

## Overview
Implements the LibLZF lossless high-speed data compression (`lzf_compress`) and decompression (`lzf_decompress`) algorithms declared in `<lzf.h>` when `CONFIG_LIBC_LZF` is enabled, including framing support for uncompressed (`Type 0`) and compressed (`Type 1`) LZF block headers.

## Interface
- `[lzf_c.c:lzf_compress]` - Compresses `in_len` bytes at `in_data` into `out_data` (up to `out_len` bytes) using a caller-supplied or internal hash table `htab`, prepending an LZF `struct lzf_header_s` framing header (`*rhdr`).
- `[lzf_d.c:lzf_decompress]` - Decompresses `in_len` bytes of raw LZF-compressed stream `in_data` into `out_data` (up to `out_len` bytes).

## Invariants
- `in_data` and `out_data` buffers passed to `[lzf_c.c:lzf_compress]` and `[lzf_d.c:lzf_decompress]` must not overlap.
- Callers of `[lzf_c.c:lzf_compress]` must reserve `LZF_TYPE1_HDR_SIZE` bytes immediately preceding `out_data` and `LZF_TYPE0_HDR_SIZE` bytes immediately preceding `in_data` because `[lzf_c.c:lzf_compress]` writes the LZF block header directly before the buffer pointer (`&((uint8_t *)out_data)[-LZF_TYPE1_HDR_SIZE]`).

## Side Effects
- `[lzf_c.c:lzf_compress]` mutates the hash table `htab` (zeroing it when `LZF_INIT_HTAB` is enabled) and writes the LZF header prior to `out_data` or `in_data`.
- `[lzf_d.c:lzf_decompress]` sets `errno` (`SET_ERRNO`) to `E2BIG` if the output buffer is too small or `EINVAL` if the compressed stream is corrupted.

## Verification
- Run: `make test`
