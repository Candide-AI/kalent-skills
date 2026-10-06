# Filters and criteria

A prompt names filter types. Call each one a filter type, or a family. It is not a criterion.

Filters build the pool: title, location, skill, language, years of experience, and the other filter types.

Criteria (`qualificationCriterias`) are subjective judgments on profiles already in the pool, for example “managed a team of fewer than 3 people”. They produce green, amber, or red. They do not build the pool. An over-specified prompt shrinks the pool because of filters, not because of criteria.

## Families, gate mode

Prompt search uses gate.

“Software engineers in Paris or Lyon who know Python and React” is three families.

- Title: software engineer, required.
- Location: Paris or Lyon. One is enough.
- Skill: Python or React. One is enough, unless the sentence says both are mandatory.

An engineer in Paris with only Python is in the pool. An engineer in Paris with neither skill is not, because the skill family is missing.

Within one family, one value is enough unless the sentence makes every value mandatory. Across families, every family must be satisfied.

## Rank

In rank, a family can stop eliminating and only affect order. Optional filters then never eliminate. The full rank write-up is not in this skill yet. For `mode`, see https://docs.kalent.ai/api-reference/search-talents.
