---
name: "supabase-v2"
displayName: "Supabase with local CLI"
description: "Build fullstack applications with Supabase's Postgres database, authentication, storage, and real-time subscriptions"
keywords: ["database", "postgres", "auth", "storage", "realtime", "backend", "supabase", "rls"]
---

# Onboarding

# Step 1: Ask user if they want to work with Supabase local or Supabase remote.

Supabase local gives users a local development environment to work with Supabase, while Supabase remote gives users a hosted environment to work with Supabase.

Supabase remote uses a remote MCP for Supabase and operates against a real environment. Tell the user that Supabase local is preferred but explain the tradeoffs for both.


# Step 2: Install MCP

If they want to use local: Follow instructions at supabase-local-onboarding.md

If they want to use remote: Follow instructions at supabase-remote-onboarding.md


# When to Load Steering Files

- Setting up a database -> 'database-setup-workflow.md'
- Writing or formatting SQL code → `supabase-code-format-sql.md`
- Writing Supabase Edge Functions (TypeScript/Deno) → `supabase-edge-functions.md`
- Creating or modifying RLS policies → `supabase-database-rls-policies.md`
- Creating PostgreSQL functions → `supabase-database-functions.md`
- Working with declarative schema (`supabase/schemas/` directory) → `supabase-declarative-database-schema.md`
- Creating migration files manually (`supabase/migrations/` directory) → `supabase-database-create-migration.md`
- Setting up or modifying Next.js authentication with Supabase SSR → `supabase-nextjs-supabase-auth.md`
- Implementing realtime features (broadcast, presence, channels, subscriptions) → `supabase-use-realtime.md`

