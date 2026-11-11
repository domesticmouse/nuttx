# NuttX Documentation Sphinx Extensions (`_extensions`)

## Overview
Custom Sphinx extensions for the NuttX documentation build system: regex-based warning log suppression and filtering (`warnings_filter.py`) and hierarchical namespace-grouped tag overview page generation (`tags_overview.py`).

## Interface
- `[warnings_filter.py:WarningsFilter]`
- `[warnings_filter.py:WarningsFilter.filter]`
- `[warnings_filter.py:Expression]`
- `[warnings_filter.py:Expression.match]`
- `[warnings_filter.py:configure]`
- `[warnings_filter.py:finished]`
- `[warnings_filter.py:setup]`
- `[tags_overview.py:write_overview]`
- `[tags_overview.py:setup]`

## Invariants
- `[warnings_filter.py:WarningsFilter.filter]` only filters log records where `record.levelno == logging.WARNING`.
- `[tags_overview.py:PRIORITY]` runs `write_overview` at priority `800` on `builder-inited` so it executes after `sphinx_tags` (default priority `500`).
- `[tags_overview.py:COLUMN_THRESHOLD]` wraps tag toctrees in multi-column `tag-columns` containers only when `len(names) >= 5`.

## Side Effects
- `[warnings_filter.py:configure]` reads `app.config.warnings_filter_config` from disk, stores `warnings_filter_expressions` on `app.env`, and inserts `WarningsFilter` at index `0` of all handlers on `logging.getLogger('sphinx')`.
- `[warnings_filter.py:WarningsFilter.filter]` mutates `record.levelno` to `logging.INFO` and prepends `'[filtered warning]: '` to `record.msg` when `self._silent` is `False`.
- `[warnings_filter.py:finished]` emits `logging.warning` for any unused filter expression when the Sphinx build finishes without exception.
- `[tags_overview.py:write_overview]` scans generated `.rst` files in `Path(app.srcdir) / app.config.tags_output_dir` and overwrites `tagsindex.rst` on disk, logging warnings for tags missing a `<namespace>:` prefix.

## Verification
- Run: `make test`
