# zds

## Overview
Host-side librarian wrapper and build rules (`tools/zds`) for the Zilog ZDS-II Windows toolchain (supporting z8, zNeo, and eZ80 targets) on Windows native and Cygwin/MSYS environments.

## Interface
- `zdsar.c:main`, `zdsar.c:parse_args`, `zdsar.c:do_archive` - CLI wrapper (`zdsar [OPTIONS] --ar "<AR>" --library "<LIBRARY>" obj [obj...]`) that converts POSIX/Windows paths (`convert_path_windows`, `convert_path_posix`), changes to the archive directory, and invokes the ZDS-II librarian with `<libname>=-+<objpath>` syntax.
- `Config.mk:PREPROCESS`, `Config.mk:COMPILE`, `Config.mk:ASSEMBLE`, `Config.mk:ARCHIVE`, `Config.mk:CLEAN` - NuttX build system macros overriding `tools/Config.mk` for ZDS-II `.obj`, `.src`, `.lst`, and `.lib` artifacts.

## Invariants
- Compiled with either `HOST_NATIVE` or `HOST_CYGWIN`; the ZDS-II librarian requires the target `.lib` archive to reside in the current working directory (`zdsar.c:main` `chdir`s to `g_libpath` before invoking `g_ar`).
- Command buffers and paths are bounded by `zdsar.c:MAX_BUFFER` (`4096`), `zdsar.c:MAX_EXPAND` (`2048`), and `zdsar.c:MAX_PATH` (`512`), inserting `zdsar.c:MAX_OBJECTS` (`1`) object per librarian invocation.

## Side Effects
- `zdsar.c:main` changes the process working directory (`chdir`) to the target library directory and executes the ZDS-II librarian via `system(g_command)` to mutate `.lib` archives on disk.

## Verification
- Run: `make test`
