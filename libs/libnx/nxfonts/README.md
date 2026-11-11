<NX Font Subsystem (`libs/libnx/nxfonts`)>
## Overview
Implements the NX bitmap font management, glyph rendering, pixel depth conversion, and LRU glyph caching subsystem. It compiles configured bitmap font definitions (`nxfonts_bitmaps.c`), provides font lookup by ID or default (`nxfonts_getfont.c`), converts 1-bit font glyphs into 1/2/4/8/16/24/32-BPP destination rasters (`nxfonts_convert.c`), and manages thread-safe reference-counted glyph caches (`nxfonts_cache.c`).

## Interface
- `nxfonts.h:struct nx_fontset_s` - Internal font set descriptor containing `struct nx_font_s` metrics and 7-bit/8-bit `struct nx_fontbitmap_s` arrays.
- `nxfonts_getfont.c:nxf_getfonthandle` - Looks up and returns an `NXHANDLE` for a specified `enum nx_fontid_e` font ID (or `NXFONT_DEFAULT`).
- `nxfonts_getfont.c:nxf_getfontset` - Returns the `struct nx_font_s` metrics descriptor for a valid font handle.
- `nxfonts_getfont.c:nxf_getbitmap` - Retrieves the `struct nx_fontbitmap_s` glyph bitmap for character code `ch` from the 7-bit or 8-bit font range.
- `nxfonts_convert.c:nxf_convert_1bpp`, `nxfonts_convert.c:nxf_convert_2bpp`, `nxfonts_convert.c:nxf_convert_4bpp`, `nxfonts_convert.c:nxf_convert_8bpp`, `nxfonts_convert.c:nxf_convert_16bpp`, `nxfonts_convert.c:nxf_convert_24bpp`, `nxfonts_convert.c:nxf_convert_32bpp` - Renders a `struct nx_fontbitmap_s` glyph into a destination line buffer at the target color depth.
- `nxfonts_cache.c:nxf_cache_connect` - Connects to an existing matching `struct nxfonts_fcache_s` instance or allocates a new glyph cache bounded by `maxglyph`.
- `nxfonts_cache.c:nxf_cache_disconnect` - Decrements the client reference count (`fclients`) on a font cache handle and frees all cached glyphs when it reaches zero.
- `nxfonts_cache.c:nxf_cache_getfonthandle` - Returns the underlying `NXHANDLE` font handle associated with an `FCACHE` instance.
- `nxfonts_cache.c:nxf_cache_getglyph` - Returns a cached `struct nxfonts_glyph_s` for character `ch`, rendering and inserting it into the LRU list on a cache miss.

## Invariants
- `nxfonts_cache.c:g_cachelock` serializes access to the global singly-linked list of font caches (`nxfonts_cache.c:g_fcaches`), and `nxfonts_cache.c:flock` (`struct nxfonts_fcache_s`) serializes per-cache glyph lookups and rendering.
- `nxfonts_cache.c:nxf_cache_disconnect`, `nxfonts_cache.c:nxf_cache_getfonthandle`, and `nxfonts_cache.c:nxf_findglyph` enforce non-NULL handles and valid reference counts (`priv->fclients > 0`) via `DEBUGASSERT`.
- `nxfonts_cache.c:nxf_renderglyph` maintains the glyph count invariant `priv->nglyphs <= priv->maxglyphs` by evicting the head (least-recently-used) glyph when full.

## Side Effects
- `nxfonts_cache.c:nxf_cache_connect`, `nxfonts_cache.c:nxf_cache_disconnect`, and `nxfonts_cache.c:nxf_renderglyph` allocate and free heap memory via `lib_zalloc`, `lib_malloc`, and `lib_free`.
- `nxfonts_cache.c:nxf_cache_connect`, `nxfonts_cache.c:nxf_cache_disconnect`, and `nxfonts_cache.c:nxf_cache_getglyph` acquire and release `nxmutex_lock` / `nxmutex_unlock` on `g_cachelock` and `priv->flock`, and mutate `errno` via `set_errno`.

## Verification
- Run: `make test`
</NX Font Subsystem (`libs/libnx/nxfonts`)>
