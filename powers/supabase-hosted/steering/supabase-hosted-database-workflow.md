# Schema managament

To update tables:

1. Call MCP `list_tables` to inspect the current schema
2. Call `apply_migration` with desired changes
3. Call MCP `get_advisors` to find and fix security/performance issues as needed with further migrations
4. Sync new migration(s) to `supabase/migrations/` locally with `supabase migration fetch --yes`
5. Generate updated types and review codebase to align usage

Assume the hosted database is the source of truth for migration history, and use CLI to sync changes to the local workspace.

# Type generation

While iterating on the schema, you should generate updated types with `supabase gen types --linked`. This outputs to stdio, so use `>` to redirect to a file.

# Troubleshooting

- Frontend error `Could not find the '<column>' column of '<table>' in the schema cache`: Update types + implementation to ensure code matches current schema
- No project ref: Run `supabase link` to link the workspace to a hosted development project
- Data not appearing in app: Run `supabase db diff --linked`. If schema drift exists run `supabase db pull <migration_name> --yes` to store changes in a new local migration and repair remote migration history. Then proceed to update types and usage.