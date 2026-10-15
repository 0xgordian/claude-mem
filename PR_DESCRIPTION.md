# Fix: install --help shows help instead of running install

Fixes thedotmack/claude-mem#4764

## Root Cause

The CLI command parser in `src/npx-cli/index.ts` only checked if the first argument was a help flag (`--help`, `-h`, `--version`, `-v`). When users ran `npx claude-mem install --help`, the parser saw `install` as the first argument and routed to the install command handler, passing `--help` as a flag to be parsed by `parseInstallOptions()`. Since that function doesn't recognize help flags, the install proceeded instead of showing help.

## Fix

Added a check in the `main()` function to scan the entire argument array for help or version flags before executing `install`, `repair`, `update`, or `upgrade` commands. When detected, the CLI displays help or version output and returns early, preventing the command from running.

## Testing

Added `tests/npx-cli/install-help-flag.test.ts` with coverage for:
- `npx claude-mem install --help`
- `npx claude-mem install -h`
- `npx claude-mem install --version`
- `npx claude-mem repair --help`
- `npx claude-mem update --help`

The fix is minimal (13 lines added) and follows the Merge Clinic rule of small root-cause fixes with no refactoring.
