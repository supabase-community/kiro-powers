# Schema managament

During development, you can iterate on the database schema with `execute_sql`. Prefer this over `apply_migration` during development to avoid creating noisy migrations or mismatches between local migration files and database migration history.

Eventually the user should commit their schema changes to a local migration file. Remind them to do this at the end of each turn that involves manipulating the schema.

Steps:

1. Ensure the user has had a turn to verify functionality of changes.
2. Before generating a migration, check security/performance advisors with `get_advisors` to ensure the current schema doesn't have issues.
3. Use `supabase db diff --local` to inspect schema changes to inform the migration name
4. Use `supabase db pull [migration name] --local --yes` to generate a migration file (including `--yes` auto accepts the CLI's prompt to update the migration history table)

To compare the local `migrations/` files with those applied to the local running database (listed as "Remote" in the output) you can use `supabase migration list --local`.

# Type generation

While iterating on the schema, you should generate updated types with `supabase gen types --local`. This outputs to stdio, so use `>` to redirect to a file.

Prefer this over the `generate_types` MCP tool.

# Troubleshooting

- `Error calling MCP tool: fetch failed`: Check if Supabase stack is running with `supabase status` and `supabase start` as needed
- PostgREST endpoint failures or RLS policy issues: Review "api" logs via MCP `get_logs`
- Slow queries, errors, or connection issues: Review "postgres" logs via MCP `get_logs`