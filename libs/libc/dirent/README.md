# Directory Stream and File Tree Walk Operations (`libs/libc/dirent`)

## Overview
Implements POSIX `<dirent.h>` directory stream management (`opendir`, `fdopendir`, `readdir`, `readdir_r`, `rewinddir`, `seekdir`, `telldir`, `closedir`, `dirfd`), directory scanning and sorting (`scandir`, `alphasort`, `versionsort`), and `<ftw.h>` recursive file tree walking (`ftw`, `nftw`).

## Interface
- `[dirent.h:dirstream]` - Internal `DIR` structure holding the underlying file descriptor `fd` and `struct dirent` entry buffer.
- `[lib_opendir.c:opendir]` - Opens a directory path and allocates a `DIR` stream.
- `[lib_fdopendir.c:fdopendir]` - Validates an open file descriptor via `fstat()` and wraps it in a `DIR` stream.
- `[lib_closedir.c:closedir]` - Closes the underlying directory descriptor and frees the `DIR` stream.
- `[lib_dirfd.c:dirfd]` - Returns the file descriptor associated with `dirp`.
- `[lib_readdir.c:readdir]` - Reads the next directory entry into `dirp->ent`.
- `[lib_readdirr.c:readdir_r]` - Thread-safe variant of `readdir` copying the entry into caller-supplied `entry`.
- `[lib_rewinddir.c:rewinddir]` - Resets the position of `dirp` to the beginning of the directory.
- `[lib_seekdir.c:seekdir]` - Sets the location in the `dirp` stream for the next `readdir` call.
- `[lib_telldir.c:telldir]` - Returns the current location associated with the `dirp` stream.
- `[lib_scandir.c:scandir]` - Scans directory `path`, filtering entries with `filter` and sorting them with `compar` via `qsort()`.
- `[lib_alphasort.c:alphasort]` - Compares two `struct dirent **` entries using `strcoll()`.
- `[lib_versionsort.c:versionsort]` - Compares two `struct dirent **` entries using `strverscmp()`.
- `[lib_ftw.c:ftw]` - Recursively descends the directory hierarchy rooted at `path`, invoking `fn` for each entry.
- `[lib_nftw.c:nftw]` - Extended file tree walk supporting `FTW_PHYS`, `FTW_MOUNT`, `FTW_CHDIR`, and `FTW_DEPTH` flags.

## Invariants
- `dirp` passed to `[lib_readdir.c:readdir]`, `[lib_readdirr.c:readdir_r]`, `[lib_closedir.c:closedir]`, `[lib_rewinddir.c:rewinddir]`, `[lib_seekdir.c:seekdir]`, `[lib_telldir.c:telldir]`, and `[lib_dirfd.c:dirfd]` must be a valid active stream; `NULL` pointers fail with `EBADF`.
- `[lib_readdir.c:readdir]` leaves `errno` unchanged when end-of-directory (`read()` returning `0`) is reached.
- `[lib_nftw.c:nftw]` enforces path lengths strictly below `PATH_MAX`, failing with `ENAMETOOLONG` otherwise.

## Side Effects
- `[lib_opendir.c:opendir]`, `[lib_fdopendir.c:fdopendir]`, `[lib_closedir.c:closedir]`, and `[lib_scandir.c:scandir]` allocate and free heap memory via `lib_malloc()`, `lib_realloc()`, and `lib_free()`.
- `[lib_opendir.c:opendir]` and `[lib_closedir.c:closedir]` exchange file descriptor ownership tags via `android_fdsan_exchange_owner_tag()` and `android_fdsan_close_with_tag()` when `CONFIG_FDSAN` is enabled.
- Performs VFS system calls (`open`, `close`, `read`, `lseek`, `fstat`, `stat`, `lstat`, `chdir`) and mutates thread `errno` on error.

## Verification
- Run: `make test`
