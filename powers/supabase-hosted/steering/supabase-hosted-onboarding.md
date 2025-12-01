# Prerequisites

Before using Supabase MCP, ensure the following are installed and running:
- Docker
- (Optionla) A Node.js package manager like npm, pnpm, bun, etc.
- Supabase CLI

## Docker Desktop

Supabase CLI requires Docker to run the local development stack.

1. Verify with: `docker version && echo "Docker is installed and running"`
2. If Docker is not installed or not running, DO NOT proceed with Supabase setup. Direct the user to install Docker Desktop first: https://www.docker.com/products/docker-desktop

## Node.js package manager

Supabase CLI should ideally be versioned as a project dependency in `package.json` "devDependencies" and managed with a Node.js package manager such as npm, pnpm, bun, etc.

1. Check if the project uses an existing package manager by looking for common lockfile formats.
2. If a package manager is not already used in the workspace, ask the user which tool they prefer to inform further installations
3. Initialize `package.json` with the appropriate tool (e.g. `npm init -y`, `pnpm init -y`, etc.)

## Supabase CLI

You MUST refer to `supabase-cli.md` and follow setup before proceeding.

# MCP setup (CLI)

Supabase CLI runs an MCP server on `http://127.0.0.1:54321/mcp`. If the user has difficulty connecting, you can verify this URL with `supabase status` (without `--local` flag). Tools executing using this server affect only the local Supabase instance, but changes can be synced to a hosted instance using the CLI.

The local MCP server supports a subset of the functionality of our hosted MCP server, since some features like edge functions are managed through the file system in local development, or may otherwise be unsupported in CLI.

Since you're working in a local editor, prefer development using this local Supabase instance. When running Supabase CLI commands, include the `--local` flag where possible to explicitly target the local instance.

# Initial setup checklist

1. Ensure Docker Desktop is running
2. Ensure Supabase CLI is installed
3. Initialize a git repo with `git init` if not already within a repo
4. Generate a basic `.gitignore` if not already present with `npx gitignore node` (substitute preferred package manager runner)
5. Run `supabase init --yes` to initialize the project (creates `supabase/` directory)
6. Run `supabase start` to start the local Supabase stack
7. Call MCP tools to get project URL and anon/publishable key
8. Create `.env.local` file with:
```
   NEXT_PUBLIC_SUPABASE_URL=<project url>
   NEXT_PUBLIC_SUPABASE_PUBLISHABLE_KEY=<anon or publishable key>
```

# Troubleshooting

- Supabase containers can't start due to port conflict: Stop existing containers with `supabase stop --all`
- MCP tools not available or connection fails: Instruct user to reconnect MCP server in Kiro's MCP Servers View (run "Kiro: Focus on MCP Servers View" from VS Code command palette)