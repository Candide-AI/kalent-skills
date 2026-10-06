# Filter flags

These flags exist only on the filter endpoint (`POST https://app.kalent.ai/api/v1/search/talents`), not on prompt search. Open this file when building the `filters` array.

- `isRequired`. `true`: this filter eliminates. `false`: it only boosts profiles that match it. In the default mode `gate`, if every value of one family is `false`, a profile that matches none of that family is still eliminated. `false` means “never eliminate” only in `rank`.
- `isExcluded`. `true` removes profiles that match. Use it for “not at X” or “not in Paris”.
- `isExactMatch`. `true`: the value as written, no fuzzy match. `false`: a near value can match. Use `true` on a title or a company name when fuzzy matching returns the wrong profiles.
- `radius`. Location filters only, in kilometers. “Within 30 km of Lyon” uses this endpoint.
- `history`. Job title and company name only. `CURRENT`, `PAST`, `CURRENT_AND_PAST`. If omitted, the engine widens to past and present (`CURRENT_AND_PAST`). Set it explicitly. `CURRENT` when the sentence has no time. `PAST` only for former or ex-. `CURRENT_AND_PAST` only when any prior stint is enough (“has been”, “has worked at”).

Accepted values (year buckets, industries, degrees, and the rest) stay on https://docs.kalent.ai/api-reference/accepted-filter-values. Do not paste them.
