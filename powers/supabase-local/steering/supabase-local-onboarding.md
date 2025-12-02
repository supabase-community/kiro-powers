# Prerequisites

Before using Supabase MCP, ensure the following are installed and running:
- Docker
- Supabase CLI
- MCP

## Docker Desktop

Supabase CLI requires Docker to run the local development stack.

1. Verify with: `docker version && echo "Docker is installed and running"`
2. If Docker is not installed or not running, DO NOT proceed with Supabase setup. Direct the user to install Docker Desktop first: https://www.docker.com/products/docker-desktop

## Supabase CLI

You MUST refer to `supabase-cli.md` and follow setup before proceeding.

## MCP

You MUST refer to `supabase-local-database-workflow.md` to understand MCP usage and setup.

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

# Hooks setup

After initial setup you MUST refer to `supabase-hooks.md` and follow instructions to set up Kiro hooks.

# Troubleshooting

- Supabase containers can't start due to port conflict: Stop existing containers with `supabase stop --all`
- MCP tools not available or connection fails: Instruct user to reconnect MCP server in Kiro's MCP Servers View (run "Kiro: Focus on MCP Servers View" from VS Code command palette)