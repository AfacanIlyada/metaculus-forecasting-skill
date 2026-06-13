# Codebook

Column-by-column documentation for the released tables. Exact column names are
left as `<TODO>` wherever they have not yet been confirmed against the actual
derived-feature file headers; do not assume a `<TODO>` name is final.

Conventions: `level` indicates the unit of observation (comment / author /
question); `type` is the storage type; `notes` documents derivation and any
leakage-safety constraints.

**Provenance note.** Confirmed column names below were read from the v1 legacy
author-level tables (`economy-business_v1.csv`, `geopolitics_v1.csv`). Those
tables predate the v2 feature set this codebook describes: they carry only four
lexical-family rates (not eight), no skill BLUPs, no six-category mix, and no
`changed_my_mind_rate` / `included_forecast_rate` / `tenure_days`. Columns that
do not exist in those tables remain `<TODO>` and must be confirmed against the
final v2 release tables. Three v1 columns have no codebook home and are not yet
placed: `polarity_abs` (absolute polarity), `has_explicit_probability`, and the
author-level `accuracy_rate` / `accuracy_group`; the v1 author key is
`username` (the codebook's `author_id`).

---

## (a) Identifiers

| column | level | type | description |
|--------|-------|------|-------------|
| `author_id` | author | int/str | Stable Metaculus author identifier. |
| `comment_id` | comment | int/str | Metaculus comment identifier. Identifier only — no comment text is released. |
| `question_id` | question | int/str | Metaculus question/post identifier. |

## (b) Outcome

| column | level | type | description |
|--------|-------|------|-------------|
| `<TODO: correctness>` | comment | bool/int | Whether the comment's stance matched the resolved outcome. |
| `<TODO: resolution>` | question | cat | Resolved outcome of the question (e.g. YES/NO). |
| `<TODO: days_to_resolution>` | comment | float | Days between comment timestamp and question resolution. Negative (post-resolution) comments excluded from accuracy analyses. |

## (c) Skill estimates

Best linear unbiased predictors (BLUPs) from the cross-classified mixed model.

| column | level | type | description |
|--------|-------|------|-------------|
| `<TODO: blup_intercept>` | author | float | Author random-intercept BLUP — overall skill level. |
| `<TODO: blup_slope_days_z>` | author | float | Author random-slope BLUP on standardized days-to-resolution (`days_z`) — how skill varies with forecast horizon. |

## (d) Text features (seventeen)

Seventeen author-aggregated text features, grouped below.

### Eight lexical families
Only four lexical-family rates are present in the v1 legacy author tables; the
other four families in the v2 set are not yet mapped.

| column | level | type | description |
|--------|-------|------|-------------|
| `hedge_rate` | author | float | Lexical family: hedging language rate. |
| `epistemic_rate` | author | float | Lexical family: epistemic-marker rate. |
| `updating_rate` | author | float | Lexical family: belief-updating language rate. |
| `causal_rate` | author | float | Lexical family: causal language rate. |
| `<TODO: lexical_5>` | author | float | Lexical family 5 (not in v1 tables). |
| `<TODO: lexical_6>` | author | float | Lexical family 6 (not in v1 tables). |
| `<TODO: lexical_7>` | author | float | Lexical family 7 (not in v1 tables). |
| `<TODO: lexical_8>` | author | float | Lexical family 8 (not in v1 tables). |

### Two density
Not present in the v1 legacy author tables; unmapped.

| column | level | type | description |
|--------|-------|------|-------------|
| `<TODO: density_1>` | author | float | Density feature 1 (not in v1 tables). |
| `<TODO: density_2>` | author | float | Density feature 2 (not in v1 tables). |

### Five structural
| column | level | type | description |
|--------|-------|------|-------------|
| `log_word_count` | author | float | Structural: log word count per comment (aggregated). |
| `sentence_count` | author | float | Structural: sentence count per comment (aggregated). |
| `avg_sentence_length` | author | float | Structural: average sentence length. |
| `flesch_reading_ease` | author | float | Structural: Flesch reading-ease score. |
| `avg_syllables_per_word` | author | float | Structural: average syllables per word. |

### Two legacy sentiment
| column | level | type | description |
|--------|-------|------|-------------|
| `polarity` | author | float | Legacy sentiment: TextBlob polarity. |
| `subjectivity` | author | float | Legacy sentiment: TextBlob subjectivity. |

## (e) Activity controls

| column | level | type | description |
|--------|-------|------|-------------|
| `n_comments` | author | int | Number of comments by the author in sample. |
| `<TODO: mean_tokens>` | author | float | Mean tokens per comment (not in v1 tables; `log_word_count` is the nearest v1 analogue but is logged word count, not token count). |
| `<TODO: category_mix_economy_business>` | author | float | Proportion of activity in economy-business (not in single-category v1 tables). |
| `<TODO: category_mix_geopolitics>` | author | float | Proportion of activity in geopolitics (not in single-category v1 tables). |
| `<TODO: category_mix_artificial_intelligence>` | author | float | Proportion of activity in artificial-intelligence (not in single-category v1 tables). |
| `<TODO: category_mix_law>` | author | float | Proportion of activity in law (not in single-category v1 tables). |
| `<TODO: category_mix_social_sciences>` | author | float | Proportion of activity in social-sciences (not in single-category v1 tables). |
| `<TODO: category_mix_elections>` | author | float | Proportion of activity in elections (not in single-category v1 tables). |
| `<TODO: changed_my_mind_rate>` | author | float | Rate of comments indicating a changed-mind (not in v1 tables; distinct from the `updating_rate` lexical feature). |
| `<TODO: included_forecast_rate>` | author | float | Rate of comments classified as containing a forecast (not in v1 tables; the v1 `has_explicit_probability` is a related but distinct explicit-numeric-probability flag). |
| `<TODO: tenure_days>` | author | float | Days between author's first and last activity, or account tenure (not in v1 tables). |
