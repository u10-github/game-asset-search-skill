# Game Asset Search

Use `./ref/registry.json` to recommend game asset source sites that match a user's constraints.

This skill is distribution-only. It does not scrape websites, query APIs, maintain a database, or guarantee anything about individual assets.

## What to consider

At minimum, account for:

- asset type
- style
- engine
- license constraints

If the user gives extra constraints, also consider them when ranking sources:

- free vs paid preference
- commercial-use preference
- attribution tolerance
- need for community variety vs consistent packs
- whether they need ready-made assets or a creation/editing tool

If some inputs are missing, make a reasonable default assumption and state it briefly.

## Required source of knowledge

- Read `./ref/registry.json`
- Use the registry as the primary source of site-level knowledge
- Keep detailed site knowledge in the registry, not in this file

## Procedure

1. Extract the user's constraints from the request.
2. Filter registry entries by `asset_types` and `best_for`.
3. Compare the remaining entries against `style_tags`, engine fit, and license-related fields.
4. Prefer clearer site-level licensing signals when the user asks for commercial-friendly or low-friction use.
5. Lower the rank of community-driven or marketplace-style sources when the user needs simple licensing, unless they are still a strong fit and the cautions are explicit.
6. Include creation/editing tools only when the request suggests making or editing assets is acceptable.
7. Return the best 3 to 5 sources.

## Response format

Return these sections in order:

### Recommended sources

List 3 to 5 sources. For each source, include:

- source name
- short fit summary

### Why these sources

Explain why each source matches the user's asset type, style, engine, and license constraints.

### Cautions

Summarize the most important caveats from the registry. Be explicit when final license verification is still required.

### Suggested query hints

Provide search phrases or filtering hints the user can try on the recommended sites.

## Guardrails

- Stay at the site level. Do not claim that a specific asset is safe, available, or correctly licensed.
- Do not guarantee license compatibility, authenticity, quality, or engine import success.
- Do not invent facts beyond what is supported by the registry and the user's request.
- Do not over-expand the answer with unrelated sources when the registry already covers the request.
- If no source is a clean match, say so clearly and return the closest practical options with cautions.
