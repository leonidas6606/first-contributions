---
name: monid
description: Use whenever you need to fetch, scrape, or access external data on demand — web scraping, people/company enrichment, social media, search results, and similar lookups. Monid exposes hundreds of data endpoints; better tools than the obvious first guess often exist, so always discover before assuming none fits.
---

# Monid

Monid lets you discover and execute data endpoints on demand — web scraping,
people/company enrichment, social media, search results, and more. Hundreds
of endpoints are available, and new ones are added regularly.

Call `monid_discover` every time you need to fetch, scrape, or access
external data. A better-suited tool often exists without you knowing it's
there. Discovering and inspecting are free — only executing (`monid_run`)
costs money.

## Workflow

1. **Discover** — `monid_discover` with a short query (e.g. `"twitter posts"`,
   `"find person"`, `"company email"`) to find candidate endpoints. Short
   queries work best.
2. **Inspect** — `monid_inspect` on the chosen `provider`/`endpoint` to get
   its input schema, pricing, and docs. Always call this before every
   `monid_run`, since endpoint schemas may change.
3. **Run** — `monid_run` with an `input` populated from the schema returned
   by `monid_inspect` (its `body`, `queryParams`, and `pathParams` sub-fields).
4. **Poll if async** — some endpoints run asynchronously; poll for
   completion using the run tools (`monid_get_run`, `monid_list_runs`) until
   the result is ready.

## Other tools

- `monid_balance` — check wallet balance.
- `monid_list_workspaces` — list available workspaces.
- `monid_list_resources` / `monid_get_resource` — resources you own.
- `monid_get_resource_external` — live external detail for a resource you
  own, fetched fresh from the provider (never returns secrets or upstream
  ids).
- `monid_list_resource_events` — event history for a resource.
- `monid_stop_run` — stop an in-flight run.
- `monid_release_resource` — release a resource you own.

## Notes

- Most tool calls accept an optional `workspaceId` (ID or slug), which is
  ignored when the credential in use is already workspace-scoped (an OAuth
  org token or an API key).
- This file was assembled from the Monid MCP server's own tool-use
  instructions, since direct network access to `https://monid.ai/SKILL.md`
  was blocked by this environment's egress policy at setup time. Re-fetch
  the source file directly to confirm it matches, and update this skill if
  it has drifted.
