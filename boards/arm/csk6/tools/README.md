# `tools` Component (`boards/arm/csk6/tools`)

## Overview
Component package providing `tools` utilities and board support files (`patch_header.py`) for the `csk6` family (`arm` architecture).

## Interface
- `[patch_header.py:DEFAULT_INPUT_FILE]` Default input binary filename `"nuttx.bin"`
- `[patch_header.py:DEFAULT_OUTPUT_FILE]` Default output binary filename `"nuttx.bin"`
- `[patch_header.py:parse_args]` CLI parser accepting `--input` and `--output`
- `[patch_header.py:patch_header]` Patches 4-byte little-endian image size and 2-byte header/vector checksums in `header_bytes`
- `[patch_header.py:patch_bin]` Reads `input_filename`, applies CSK6 ROM boot header checksums, and writes `output_filename`
- `[patch_header.py:main]` CLI entry point invoking `parse_args()` and `patch_bin()`

## Invariants
- `[patch_header.py:_IMAGE_START]` Header checksum region starts at byte offset `192` (`_IMAGE_SIZE_OFFSET = 196`, `_IMAGE_HDR_CHK_OFFSET = 252`, `_IMAGE_HEADER_SIZE = 256`)
- `[patch_header.py:_get_header_sum]` Input image must be at least 252 bytes; `header_sum` sums bytes `[192, 252)` and `vector_sum` sums bytes `[0, 252)` plus `(header_sum & 0xFF) + ((header_sum >> 8) & 0xFF)`

## Side Effects
- `[patch_header.py:patch_bin]` Reads binary file `input_filename`, overwrites `output_filename` (`nuttx.bin` by default) with patched ROM boot tag, and prints status to stdout

## Verification
- Run: `./tools/configure.sh sim:nsh && make`
