# Git CODEOWNERS Generator

## Overview
Analyzes git commit history across tracked files in the NuttX repository to compute contributor line-change statistics and generate a GitHub-compatible `CODEOWNERS` roster printed to standard output.

## Interface
- `codeowners.py:Ownership` - Data class representing an author's (`owner`) total line modifications (`changes`) for a given file (`path`).
- `codeowners.py:get_owners`, `codeowners.py:parse_change_count`, `codeowners.py:sort_by_changes`, `codeowners.py:filter_owners` - Queries `git log --pretty="%ae" --shortstat` for a file path, sums insertions/deletions per author email, sorts descending by change count, and filters ignored emails.
- `codeowners.py:get_files`, `codeowners.py:parse_ignore_list`, `codeowners.py:generate_codeowners`, `codeowners.py:main` - Lists tracked repository files excluding `IGNORE_LOCS`, parses an optional ignore file (`codeowners-ignore.txt`), maps `get_owners` across a `multiprocessing.Pool` (`N_PROCESSES = 20`), retains `TOP_N_AUTHORS = 5`, and prints the resulting `CODEOWNERS` lines.

## Invariants
- `codeowners.py:main` must be executed from the root of the git repository (checks for `.git` in `os.listdir()`).
- At most `codeowners.py:TOP_N_AUTHORS` (5) authors per file are selected prior to filtering against the ignore list (`codeowners-ignore.txt`).

## Side Effects
- Spawns `git ls-files` (`codeowners.py:get_files`) and parallel `git --no-pager log` subprocesses across 20 worker processes (`codeowners.py:get_owners`, `codeowners.py:main`).
- Reads the optional ignore list file from `sys.argv[1]` (`codeowners.py:parse_ignore_list`) and writes the generated `CODEOWNERS` table to stdout (`codeowners.py:generate_codeowners`).

## Verification
- Run: `make test`
