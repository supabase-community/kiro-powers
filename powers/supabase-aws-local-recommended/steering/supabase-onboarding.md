---
inclusion: manual
---

# Prerequisites

Before using Supabase MCP, ensure the following are installed and running:

- **Docker Desktop**: Supabase CLI requires Docker to run the local development stack
  - Verify with: `docker --version`
  - Docker daemon must be running before starting Supabase
  - **CRITICAL**: If Docker is not installed or not running, DO NOT proceed with Supabase setup. Direct the user to install Docker Desktop first: https://www.docker.com/products/docker-desktop
- **Supabase CLI**: Install via npm, Homebrew, or other package managers
  - Verify with: `supabase --version`
  - Installation docs: https://supabase.com/docs/guides/cli/getting-started

# MCP setup (CLI)

Supabase CLI runs an MCP server on `http://127.0.0.1:54321/mcp`. If the user has difficulty connecting, you can verify this URL with `supabase status` (without `--local` flag). Tools executing using this server affect only the local Supabase instance, but changes can be synced to a hosted instance using the CLI.

The local MCP server supports a subset of the functionality of our hosted MCP server, since some features like edge functions are managed through the file system in local development, or may otherwise be unsupported in CLI.

Since you're working in a local editor, prefer development using this local Supabase instance. When running Supabase CLI commands, include the `--local` flag where possible to explicitly target the local instance.

# Initial setup checklist

**STOP**: Before proceeding, verify Docker is installed and running with `docker --version`. If this command fails, the user must install Docker Desktop before continuing.

1. Ensure Docker Desktop is running
2. Run `supabase init` to initialize the project (creates `supabase/` directory)
3. Run `supabase start --local` to start the local Supabase stack
4. Run `supabase status` to get connection details (API URL and anon key)
5. Create `.env.local` file with:
```
   NEXT_PUBLIC_SUPABASE_URL=<API URL from status>
   NEXT_PUBLIC_SUPABASE_ANON_KEY=<anon key from status>
```
6. Verify MCP connection is working