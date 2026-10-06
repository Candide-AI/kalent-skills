# Qualified search

Start returns HTTP 202, a casting id, and status `running`.

- `POST https://app.kalent.ai/api/v1/search/talents/qualified`
- `POST https://app.kalent.ai/api/v1/search/talents/qualified/by-prompt`

Two ways to follow, both valid:

- Poll `GET https://app.kalent.ai/api/v1/search/talents/qualified/{castingId}` every 10–20 seconds while `nextAction` is `wait`.
- Or set `webhook.url`. HTTPS only. Not localhost, not a private address, not a metadata address.

Webhook events: `talent_judged`, `wave_finished`, `pool_exhausted`. The GET response is the source of truth. Webhooks are notifications. Kalent does not sign payloads. A shared secret goes through custom parameters if one is needed. See https://docs.kalent.ai/api-reference/qualified-search-overview.

`nextAction`: `wait`, `continue`, `retry`, `done`.

Two API credits per judged profile, including red. Profiles opened but not judged are not charged.
