# pynuttx

## Overview
Python GDB bootstrap package (`tools/pynuttx`) for debugging Apache NuttX kernels, core dumps, and live targets. Provides the top-level `gdbinit.py` entry script and houses the `nxgdb` Python package.

## Interface
- `gdbinit.py:here` - GDB initialization script that prepends `tools/pynuttx` to `sys.path`, reloads any cached `nxgdb` modules in `sys.modules`, and imports `nxgdb`.
- [./nxgdb/README.md](./nxgdb/README.md) - NuttX GDB Python extension package (`nxgdb`) providing thread inspection, memory/MMU analysis, crash dump diagnostics, and hardware register/protocol helpers.

## Invariants
- Must be executed inside a Python-enabled GDB environment (`gdbinit.py` imports `nxgdb`, which depends on the `gdb` Python module).

## Side Effects
- Mutates `sys.path` and purges/re-imports `nxgdb*` entries in `sys.modules` when sourced by GDB.

## Verification
- Run: `make test`
