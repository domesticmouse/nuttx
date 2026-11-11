# NuttX Documentation (`Documentation`)

## Overview
Sphinx documentation configuration (`conf.py`) and URL redirect mapping (`redirects.py`) for moved, renamed, or merged NuttX documentation pages and tags, along with custom Sphinx build extensions in `_extensions`.

## Interface
- `[conf.py:project]`
- `[conf.py:copyright]`
- `[conf.py:author]`
- `[conf.py:version]`
- `[conf.py:release]`
- `[conf.py:extensions]`
- `[conf.py:source_suffix]`
- `[conf.py:todo_include_todos]`
- `[conf.py:autosectionlabel_prefix_document]`
- `[conf.py:suppress_warnings]`
- `[conf.py:highlight_language]`
- `[conf.py:primary_domain]`
- `[conf.py:templates_path]`
- `[conf.py:exclude_patterns]`
- `[conf.py:html_theme]`
- `[conf.py:html_show_sphinx]`
- `[conf.py:html_theme_options]`
- `[conf.py:html_context]`
- `[conf.py:html_static_path]`
- `[conf.py:html_css_files]`
- `[conf.py:html_show_license]`
- `[conf.py:html_logo]`
- `[conf.py:html_favicon]`
- `[conf.py:today_fmt]`
- `[conf.py:c_id_attributes]`
- `[conf.py:sphinx_tabs_valid_builders]`
- `[conf.py:linkcheck_ignore]`
- `[conf.py:latex_engine]`
- `[conf.py:copybutton_exclude]`
- `[conf.py:warnings_filter_config]`
- `[conf.py:tags_create_tags]`
- `[conf.py:tags_page_title]`
- `[conf.py:tags_page_header]`
- `[conf.py:tags_overview_title]`
- `[conf.py:tags_create_badges]`
- `[conf.py:tags_badge_colors]`
- `[conf.py:redirect_html_template_file]`
- `[redirects.py:redirects]`
- `[redirects.py:_moved]`
- `[redirects.py:_moved_trees]`
- [`_extensions`](./_extensions/README.md) - Custom Sphinx extensions for warning filtering and tag overview generation.

## Invariants
- No duplicate old document path keys are allowed in the redirect mapping (`assert old not in out`) `[redirects.py:_moved]`.
- Every renamed, moved, or merged documentation page must have an entry in `redirects` `[redirects.py:redirects]`.
- Pages listed in `_NOT_IN_OLD_TREE` are excluded from automatic directory tree redirect expansion `[redirects.py:_moved_trees]`.

## Side Effects
- Mutates `sys.path` by inserting `_extensions` and `.` at index `0` `[conf.py:sys.path]`.
- Reads `SOURCE_DATE_EPOCH` from `os.environ` and globs `ReleaseNotes/NuttX-*.md` at import time `[conf.py:_build_year]`.
- Scans `Documentation/os/*` subdirectories via `rglob('*.rst')` at import time to build `_OS_TREES` redirects `[redirects.py:_moved_trees]`.

## Verification
- Run: `make test`
