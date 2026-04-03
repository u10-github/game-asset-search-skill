---
name: game-asset-search
description: Recommend and compare site-level sources for game assets based on asset type, style, engine fit, and license constraints. Use when Codex needs to help a user find places to browse or obtain 2D, 3D, UI, texture, audio, animation, or pixel-art workflow assets or tools, especially when the user cares about commercial-use friction, attribution, free-vs-paid preference, or marketplace-vs-curated tradeoffs.
---

# Game Asset Search

Use `./ref/registry.json` as the primary source of knowledge.

This skill is distribution-only. It does not scrape websites, query APIs, maintain a database, verify live listings, or guarantee anything about individual assets.

## Read first

- Read `./ref/registry.json` before recommending sources.
- Keep site-specific facts in the registry, not in this file.
- Stay at the site level unless the user explicitly asks for example search phrases.

## Extract constraints

Capture these inputs when present:

- asset type
- visual or audio style
- target engine or workflow
- license or commercial-use constraints

Also use these tie-breakers when the user provides them:

- free vs paid preference
- attribution tolerance
- curated packs vs marketplace variety
- ready-made assets vs creation/editing tools

If key inputs are missing, make a reasonable default assumption and state it briefly.

## Rank sources

1. Filter registry entries by `asset_types` and `best_for`.
2. Compare remaining entries against `style_tags`, engine fit, and workflow fit.
3. Prefer sources with clearer license signals when the user wants commercial-friendly or low-friction use.
4. Lower the rank of community or marketplace sources when the user wants simple licensing, unless they are still the strongest match and the caveats are explicit.
5. Recommend creation or editing tools only when the user is open to making, editing, or adapting assets instead of only downloading ready-made packs.
6. Return the best 3 to 5 sources. If there is no clean match, say so and provide the closest practical options.

## Respond

Return these sections in order:

### Recommended sources

List 3 to 5 sources. For each source, include:

- source name
- short fit summary

### Why these sources

Explain how each source matches the user's asset type, style, engine, and license needs.

### Cautions

Summarize the most important caveats from the registry. Be explicit when final license verification is still required.

### Suggested query hints

Provide search phrases or filtering hints the user can try on the recommended sites.

## Guardrails

- Do not claim that a specific asset is safe, available, or correctly licensed.
- Do not guarantee license compatibility, authenticity, quality, or engine import success.
- Do not invent facts beyond the registry and the user's request.
- Do not pad the answer with unrelated sources when the registry already covers the request.
