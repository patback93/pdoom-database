# The p(doom) database

Every public, self-stated estimate of **p(doom)**: the probability that advanced AI ends in human extinction or a comparable, irreversible catastrophe. One row per statement. Every row has a source you can click.

Live, sortable version: **https://pdoomcoin.lol/pdoom**
Raw data: `pdoom.json` (also served at https://pdoomcoin.lol/data/pdoom.json)

## Rules

1. **Self-stated only.** The person said the number, in public, themselves. No inference, no "reportedly."
2. **Quoted as given.** Ranges stay ranges. ">10%" stays ">10%". We do not round, average, or interpret.
3. **Scope and horizon recorded when stated.** "Extinction this decade" and "catastrophe by 2100" are different claims and are labeled as such.
4. **Changed your mind? New row.** Earlier statements are never overwritten. The database is a record, not a scoreboard.
5. **Verified means re-checked.** `"verified": true` means a maintainer opened the primary source and confirmed the quote. Rows from secondary lists are included with their citations and marked `false` until checked.
6. **No side taken.** Yampolskiy's 99.999999% and LeCun's <0.01% are both in here on equal terms.

## Who's included (widened Sept 29, 2026)

The bar for what a row *is* hasn't moved: a number the person said themselves, in public, with a link a stranger can check. The bar for *who* can have a row is wider, so the sample isn't just the AI-safety world talking to itself.

**In:**
- Any real, identifiable person, whatever their field: researchers, builders, investors, officials, journalists, founders, public figures.
- Established public pseudonyms with a real audience (roughly 10k+ followers or a known byline), tagged as such.
- Conditional numbers, with the condition kept in `scope` or `note`.
- Plain words that *are* a number: "zero", "none", "certain", "basically zero". Recorded as said (≈0%), like LeCun and Huang.
- Statements in any language, with the original words in `quote_original` and an English translation in `quote`.
- A number given as a direct answer to "what's your p(doom)?", in any medium, including replies on X.

**Out:**
- Numbers someone else attributed to the person.
- Vague words ("unlikely", "a real risk", "not zero"). If the person was asked directly and answered like this, they go in `declined`.
- Anonymous one-off accounts and first-name-only callers.
- Numbers about something else, such as doom *without* AI, or the odds of AGI by a date.

The p(doom) index uses one number per person (their latest) and excludes surveys, markets, polls and models. Widening the net changes who is counted, so every sweep that adds people is logged in the CHANGELOG with the before and after median.

## Schema

| field | meaning |
|---|---|
| `name` | person, or group for surveys |
| `role` | affiliation or description at the time of the statement |
| `stake` | the speaker's relationship to the AI industry, one of `lab`, `ex-lab`, `ai-industry`, `investor`, `safety-org`, `academic`, `government`, `media`, `independent` (null for surveys). Public affiliation only, never money. Definitions in `stake_legend` in the JSON. |
| `low`, `high` | numeric bounds in percent; `high` = 100 for open-ended ">X%" |
| `label` | the value as the speaker gave it |
| `scope` | what "doom" meant in context |
| `horizon` | time frame, if stated |
| `quote` | exact words, when available (English translation for non-English statements) |
| `quote_original` | the original words, for non-English statements |
| `source_url`, `source_type` | where to hear or read it |
| `date` | ISO date of the statement (X posts: derived from the tweet ID) |
| `verified` | re-checked against the primary source by a maintainer |
| `tags` | `lab`, `ex-lab`, `researcher`, `safety`, `academic`, `survey`, `poll`, `market`, `model`, `forecaster`, `founder`, `investor`, `policy`, `writer`, `advocate`, `podcaster`. `survey`, `market` and `model` rows are excluded from the median; `model` means an AI system's own answer, not a person's. |
| `note` | caveats the speaker attached |

## Contributing

Open an issue using the **New estimate** template, or send a pull request editing `pdoom.json`. Include the exact quote and a link where a stranger can confirm it. Submissions without a primary source are not merged.

## Citing

> The p(doom) database, pdoomcoin.lol, retrieved YYYY-MM-DD. CC-BY-4.0.

## Who isn't here, and why

Robin Hanson's "<1%" was a podcast host's characterization, not his words, so he has no row. People who were asked for a number on the record and did not give one (Demis Hassabis, Sundar Pichai, Neel Nanda, Stuart Russell, Eliezer Yudkowsky and others) are listed in the `declined` array with their words. Refusals are not numbers, so they are not rows. Public-opinion polls are tagged `survey` and `poll`; their labels are shares of respondents, not probabilities, and they are excluded from the median.

## Provenance

Seeded from PauseAI's p(doom) list (re-sourced) and the estimates on pdoomcoin.lol's board. Maintained by the p(doom) project. The coin is a memecoin; the data is not.
