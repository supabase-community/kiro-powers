Supabase CLI runs and interacts with Supabase stack locally.

CLI may be installed globally (e.g. with homebrew or scoop) or as a project dependency  (e.g. in "devDependency" with npm, pnpm, bun, etc.).
Prefer using it as a project dependency to keep CLI version pinned in your development environment.

# CLI Setup

1. Check if the workspace has a package manager. If none is installed, ask the user which package manager they'd like to use
2. Verify CLI is installed with `[prefix?] supabase --version` using appropriate package manager prefix if applicable
3. If not installed, ask the user for their preferred package manager and install it as a "devDependency"

**Note for pnpm:**

pnpm requires a manual `approve-builds` step (or approval via config) to generate the `.bin/supabase` entry.

Before installing with pnpm, add to `pnpm-workspace.yaml`:
```yaml
onlyBuiltDependencies:
  - supabase
```

# CLI Usage

For npm and similar Node package managers, `supabase` commands MUST be prefixed with the package manager's command runner.
- npm: `npx supabase ...`
- pnpm: `pnpm supabase ...`
- bun: `bun supabase ...`
Look for project lockfiles or ask the user to determine the appropriate package manager.

**IMPORTANT** Every time a bare `supabase` command is mentioned, consider which prefix is needed and add it accordingly.

# Troubleshooting 

For further troubleshooting, direct the user to: https://supabase.com/docs/guides/cli/getting-started
