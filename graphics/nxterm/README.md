# NX Terminal Driver (`graphics/nxterm`)

## Overview
Implements the NxTerm character console driver (`/dev/nxtermN`), enabling standard POSIX character I/O, VT100 escape sequence processing, font glyph caching, automatic line wrapping, vertical scrolling, and optional per-window keyboard input (`CONFIG_NXTERM_NXKBDIN`) on top of raw NX windows (`NXWINDOW`), framed NXTK client sub-windows (`NXTKWINDOW`), or NXTK toolbars.

## Interface
- `[nxterm.h:struct nxterm_state_s]` - Per-instance console driver state structure holding window operations, font cache (`FCACHE`), displayed character bitmap array (`bm[CONFIG_NXTERM_MXCHARS]`), VT100 sequence buffer, and keyboard ring buffer
- `[nxterm.h:struct nxterm_operations_s]` - Polymorphic window rendering vtable (`fill`, `move`, `bitmap`) abstracting raw NX windows, NXTK client windows, and NXTK toolbars
- `[nxterm.h:struct nxterm_bitmap_s]` - Positioned character code and glyph flag descriptor (`BMFLAGS_NOGLYPH`)
- `[nxterm.h:enum nxterm_vt100state_e]` - VT100 parser state return codes (`VT100_NOT_CONSUMED`, `VT100_CONSUMED`, `VT100_PROCESSED`, `VT100_ABORT`)
- `[nxterm_driver.c:g_nxterm_drvrops]` - VFS `struct file_operations` table (`nxterm_open`, `nxterm_close`, `nxterm_read`, `nxterm_write`, `nxterm_ioctl`, `nxterm_poll`, `nxterm_unlink`)
- `[nx_register.c:nx_register]` - Registers `/dev/nxtermN` bound to a raw NX window (`NXWINDOW`) via `nx_fill`, `nx_move`, and `nx_bitmap`
- `[nxtk_register.c:nxtk_register]` - Registers `/dev/nxtermN` bound to a framed NXTK window (`NXTKWINDOW`) via `nxtk_fillwindow`, `nxtk_movewindow`, and `nxtk_bitmapwindow`
- `[nxtool_register.c:nxtool_register]` - Registers `/dev/nxtermN` bound to an NXTK toolbar (`NXTKWINDOW`) via `nxtk_filltoolbar`, `nxtk_movetoolbar`, and `nxtk_bitmaptoolbar`
- `[nxterm_register.c:nxterm_register]` - Allocates `struct nxterm_state_s`, connects to the font cache (`nxf_cache_connect`), clears the window, draws the initial cursor, and registers `/dev/nxtermN`
- `[nxterm_unregister.c:nxterm_unregister]` - Disconnects the font cache, unregisters `/dev/nxtermN`, destroys locks/semaphores, and frees `struct nxterm_state_s`
- `[nxterm_driver.c:nxterm_ioctl_tap]` - Dispatches `NXTERMIOC_NXTERM_REDRAW`, `NXTERMIOC_NXTERM_KBDIN`, and `NXTERMIOC_NXTERM_RESIZE` commands from VFS `ioctl` or external callers (`boardctl`)
- `[nxterm_redraw.c:nxterm_redraw]` - Redraws the background and all cached character glyphs (`priv->bm[]`) intersecting `rect`
- `[nxterm_resize.c:nxterm_resize]` - Updates the terminal window dimensions (`priv->wndo.wsize`)
- `[nxterm_kbdin.c:nxterm_kbdin]`, `[nxterm_kbdin.c:nxterm_read]`, `[nxterm_kbdin.c:nxterm_poll]` - Enqueues incoming keyboard bytes into `priv->rxbuffer`, wakes blocked readers (`priv->waitsem`), and services VFS `read` and `poll` (`CONFIG_NXTERM_NXKBDIN`)
- `[nxterm_putc.c:nxterm_putc]`, `[nxterm_putc.c:nxterm_showcursor]`, `[nxterm_putc.c:nxterm_hidecursor]` - Renders characters and the cursor glyph (`CONFIG_NXTERM_CURSORCHAR`), handling `\r`, `\n`, backspace/delete, line wrapping, and scrolling
- `[nxterm_font.c:nxterm_addchar]`, `[nxterm_font.c:nxterm_hidechar]`, `[nxterm_font.c:nxterm_backspace]`, `[nxterm_font.c:nxterm_home]`, `[nxterm_font.c:nxterm_newline]`, `[nxterm_font.c:nxterm_fillchar]` - Character glyph placement, lookup, erasure, and bitmap blitting helpers
- `[nxterm_clear.c:nxterm_clear]`, `[nxterm_scroll.c:nxterm_scroll]` - Full-window background clear and vertical scroll handlers
- `[nxterm_vt100.c:nxterm_vt100]`, `[nxterm_vt100.c:nxterm_vt100part]` - Incremental VT100 escape sequence recognizer handling erase-to-EOL (`<esc>[K`), cursor left (`<esc>[D`), cursor right (`<esc>[C`), and ANSI SGR attribute sequences (`<esc>[...m`)

## Invariants
- `[nxterm_register.c:nxterm_register]` asserts `handle != NULL`, `wndo != NULL`, `ops != NULL`, and `(unsigned)minor < 256`.
- Without `CONFIG_NXTERM_NXKBDIN`, `[nxterm_driver.c:nxterm_open]` rejects any open mode other than `O_WRONLY` with `-EACCES`.
- Displayed character metadata is bounded by `priv->nchars <= priv->maxchars` (`CONFIG_NXTERM_MXCHARS`); scrolling (`[nxterm_scroll.c:nxterm_scroll]`) and erase-to-EOL (`[nxterm_vt100.c:nxterm_erasetoeol]`) compact `priv->bm[]` in place to keep redraw state synchronized with the screen.
- Buffered VT100 escape sequences never exceed `VT100_MAX_SEQUENCE` (`32` bytes).

## Side Effects
- Allocates and frees driver state on the kernel heap via `kmm_zalloc` and `kmm_free`, and registers/unregisters character device nodes `/dev/nxtermN` (`[nxterm_register.c:nxterm_register]`, `[nxterm_unregister.c:nxterm_unregister]`).
- Acquires per-device mutex `priv->lock` across display mutations and keyboard buffer operations, and acquires interrupt-saving spinlock `priv->spinlock` during `poll_notify` (`[nxterm_kbdin.c:nxterm_pollnotify]`, `[nxterm_kbdin.c:nxterm_poll]`).
- Invokes NX/NXTK window rendering callbacks (`priv->ops->fill`, `priv->ops->move`, `priv->ops->bitmap`) and font cache operations (`nxf_cache_connect`, `nxf_cache_disconnect`, `nxf_cache_getglyph`).

## Verification
- Run: `make test`
