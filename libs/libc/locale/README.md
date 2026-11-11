# Locale, Message Catalogs, Gettext, and Iconv (`libs/libc/locale`)

## Overview
Implements POSIX `<locale.h>`, `<langinfo.h>`, `<nl_types.h>`, `<libintl.h>`, and `<iconv.h>` localization support in `libc` (`CONFIG_LIBC_LOCALE`). Provides locale selection and formatting queries (`setlocale`, `localeconv`, `nl_langinfo`, `newlocale`, `duplocale`, `freelocale`, `uselocale`), X/Open message catalogs (`catopen`, `catgets`, `catclose`), GNU `gettext` binary `.mo` translation lookups, and stateful character set conversion (`iconv_open`, `iconv`, `iconv_close`) across UTF-8, UTF-16, UTF-32, UCS-2, ASCII, ISO-8859, KOI8, and CJK encodings.

## Interface
- `[lib_setlocale.c:setlocale]`, `[lib_newlocale.c:newlocale]`, `[lib_duplocale.c:duplocale]`, `[lib_freelocale.c:freelocale]`, `[lib_uselocale.c:uselocale]`, `[lib_getlocalename_l.c:getlocalename_l]` - Configures and queries process/thread locale handles (`"C"`, `"POSIX"`, `"C.UTF-8"`).
- `[lib_localeconv.c:localeconv]` - Returns a pointer to the `struct lconv` numeric and monetary formatting conventions for the current locale.
- `[lib_langinfo.c:nl_langinfo]` - Returns locale string constants (`CODESET`, day/month names, `RADIXCHAR`, `YESEXPR`, `NOEXPR`) for `nl_item`.
- `[lib_maxlocale.c:__locale_mb_cur_max]` - Returns the maximum multibyte character length (`1`) for the current locale.
- `[lib_catalog.c:catopen]`, `[lib_catalog.c:catgets]`, `[lib_catalog.c:catclose]` - Opens, queries (via binary search), and closes memory-mapped X/Open `.cat` message catalog files (`CONFIG_LIBC_LOCALE_CATALOG`).
- `[lib_gettext.c:gettext]`, `[lib_gettext.c:dgettext]`, `[lib_gettext.c:dcgettext]`, `[lib_gettext.c:ngettext]`, `[lib_gettext.c:dngettext]`, `[lib_gettext.c:dcngettext]` - Translates singular and plural message strings using cached GNU `.mo` files and plural-rule evaluation (`CONFIG_LIBC_LOCALE_GETTEXT`).
- `[lib_gettext.c:textdomain]`, `[lib_gettext.c:bindtextdomain]`, `[lib_gettext.c:bind_textdomain_codeset]` - Sets or queries the active message domain and base directory binding for `gettext`.
- `[lib_iconv.c:iconv_open]`, `[lib_iconv.c:iconv]`, `[lib_iconv.c:iconv_close]` - Allocates a character encoding conversion descriptor, converts multibyte character buffers, and closes the descriptor (`CONFIG_LIBC_LOCALE_ICONV`).

## Invariants
- `[lib_setlocale.c:setlocale]` and `[lib_newlocale.c:newlocale]` only accept `"C"`, `"POSIX"`, `""`, `"C.UTF-8"`, or `"C.utf8"`.
- `[lib_gettext.c:dcngettext]` saves and restores the caller's `errno` so translation lookups never clobber `errno` when returning fallback `msgid1`/`msgid2` strings.
- `[lib_catalog.c:catopen]` verifies the big-endian catalog magic header `0xff88ff89` before accepting a catalog file.

## Side Effects
- `[lib_catalog.c:catopen]`, `[lib_catalog.c:catclose]`, and `[lib_gettext.c:dcngettext]` open catalog/`.mo` files from `CONFIG_LIBC_LOCALE_PATH`, map them into memory via `mmap()`, and unmap them via `munmap()`.
- `[lib_gettext.c:dcngettext]` caches loaded `.mo` files in the global `g_mofile` list protected by mutex `g_lock` (`nxmutex_lock` / `nxmutex_unlock`).
- `[lib_gettext.c:textdomain]` mutates the current task group's `ta_domain` buffer (`tls_get_info()->tl_task->ta_domain`).
- `[lib_iconv.c:iconv_open]` and `[lib_iconv.c:iconv]` set thread `errno` (`EINVAL`, `EILSEQ`, `E2BIG`, `ENOMEM`) on encoding or buffer errors.

## Verification
- Run: `make test`
