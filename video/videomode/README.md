# NuttX Video Mode and EDID Library (`videomode`)

## Overview
Display timing and EDID utility library (built when `CONFIG_VIDEO_EDID` is enabled): 128-byte EDID block parsing and syslog dumping (`edid_parse.c`, `edid_dump.c`), VESA Generalized Timing Formula calculation (`vesagtf.c`), and DMT video mode lookup, sorting, and syslog dumping (`videomode_lookup.c`, `videomode_sort.c`, `videomode_dump.c`).

## Interface
- `[edid_parse.c:edid_parse]`
- `[edid_dump.c:edid_dump]`
- `[videomode_lookup.c:videomode_lookup_by_name]`
- `[videomode_sort.c:sort_videomodes]`
- `[videomode_dump.c:videomode_dump]`
- `[vesagtf.c:vesagtf_mode_params]`
- `[vesagtf.c:vesagtf_mode]`

## Invariants
- `[edid_parse.c:edid_is_valid]` requires the 8-byte `EDID_MAGIC` signature at offset `0` and the 128-byte block checksum to equal `0 mod 256`, returning `-EINVAL` otherwise.
- `[videomode_sort.c:sort_videomodes]` leaves the `modes` array unchanged if `nmodes < 2` and always places `*preferred` at index `0` when `*preferred != NULL`.
- `[vesagtf.c:vesagtf_mode_params]` returns `-EINVAL` if refresh rate `v < 1`.

## Side Effects
- `[edid_parse.c:edid_parse]` populates caller-provided `struct edid_info_s *edid` and sorts `edid->edid_modes` in-place via `sort_videomodes`.
- `[videomode_sort.c:sort_videomodes]` mutates the `modes` array and updates `*preferred` in-place.
- `[edid_dump.c:edid_dump]` and `[videomode_dump.c:videomode_dump]` write formatted EDID and video mode timing information to `syslog(LOG_INFO, ...)`.

## Verification
- Run: `make test`
