---
name: build-with-kalent
description: "Call the Kalent HTTP API from a coding agent. Use for prompt search, pagination, filters versus criteria, filter flags, or a qualified search followed by polling or a webhook."
metadata:
  docs: "https://docs.kalent.ai"
---

# Build with Kalent

HTTP only (`fetch` or `curl`). There is no SDK.

Base URL: `https://app.kalent.ai`. Call the paths under `/api/v1`.

Read the API key from the environment variable `KALENT_API_KEY` and send it as the header `x-api-key`. Never take the key from the chat. Never commit it.

The same workspace API key has two balances: search spends API credits and does not need a Kalent subscription, and enrichment spends contact credits and still needs an active or trialing subscription.

Docs are canonical. Link them. Do not paste request or response schemas from memory.

- https://docs.kalent.ai
- https://docs.kalent.ai/llms.txt
- https://docs.kalent.ai/api-reference/search-talents-by-prompt
- https://docs.kalent.ai/api-reference/search-talents
- https://docs.kalent.ai/api-reference/accepted-filter-values
- https://docs.kalent.ai/api-reference/qualified-search-overview

## Which call

While a sentence is enough, stay on prompt search.

Open `references/filters.md` when the need is an optional preference, an exclusion, an exact match, a radius, or current versus past.

- **Prompt search (default).** `POST https://app.kalent.ai/api/v1/search/talents/by-prompt`. Search talents by prompt. Behaves as gate.
- **Filter search.** `POST https://app.kalent.ai/api/v1/search/talents` with a `filters` array, when the flags in `references/filters.md` are needed.
- **Qualified search.** Start returns `202` with a casting id and status `running`. Results arrive by polling or webhook. See `references/qualified-search.md`.

## References

| File | Open it when |
| --- | --- |
| [references/pagination.md](references/pagination.md) | A search may need another page |
| [references/filters-and-criteria.md](references/filters-and-criteria.md) | You are writing a prompt, or deciding what builds the pool |
| [references/filters.md](references/filters.md) | You are building the `filters` array |
| [references/qualified-search.md](references/qualified-search.md) | You need green, amber, or red judgments |
