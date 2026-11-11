# Universally Unique Identifiers (`libs/libc/uuid`)

## Overview
Implements DCE 1.1 / RFC 4122 UUID (`uuid_t`) generation, string formatting and parsing, comparison, hashing, nil-UUID handling, and big-endian/little-endian binary stream encoding and decoding (`<uuid.h>`).

## Interface
- `lib_uuid_create.c:uuid_create` - Generates a random RFC 4122 Version 4 UUID using `arc4random_buf`.
- `lib_uuid_create_nil.c:uuid_create_nil`, `lib_uuid_is_nil.c:uuid_is_nil` - Initializes a all-zero nil UUID or tests whether a UUID is nil.
- `lib_uuid_compare.c:uuid_compare`, `lib_uuid_equal.c:uuid_equal` - Lexicographically compares two `uuid_t` structures (`-1`, `0`, `1`) or tests equality (`1` or `0`), treating `NULL` pointers as nil UUIDs.
- `lib_uuid_from_string.c:uuid_from_string`, `lib_uuid_to_string.c:uuid_to_string` - Parses a 36-character hyphenated UUID string (`xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx`) into `uuid_t` or formats a `uuid_t` into a newly allocated string (`asprintf`).
- `lib_uuid_hash.c:uuid_hash` - Computes a 16-bit hash value over a `uuid_t`.
- `lib_uuid_stream.c:uuid_enc_le`, `lib_uuid_stream.c:uuid_dec_le`, `lib_uuid_stream.c:uuid_enc_be`, `lib_uuid_stream.c:uuid_dec_be` - Serializes and deserializes `uuid_t` fields to and from packed 16-byte little-endian or big-endian byte buffers.

## Invariants
- `lib_uuid_create.c:uuid_create` sets the RFC 4122 variant bits (`clock_seq_hi_and_reserved = (clock_seq_hi_and_reserved & 0x3f) | 0x80`) and Version 4 bits (`time_hi_and_version = (time_hi_and_version & 0x0fff) | 0x4000`).
- Functions taking `FAR uint32_t *status` write `uuid_s_ok` (or `uuid_s_invalid_string_uuid` / `uuid_s_no_memory`) when `status != NULL`.

## Side Effects
- `lib_uuid_create.c:uuid_create` consumes random entropy via `arc4random_buf`.
- `lib_uuid_to_string.c:uuid_to_string` allocates the output string `*s` on the heap via `asprintf` (or `strdup` for nil UUIDs).

## Verification
- Run: `make test`
