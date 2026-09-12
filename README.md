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

## Schema

| field | meaning |
|---|---|
| `name` | person, or group for surveys |
| `role` | affiliation or description at the time of the statement |
| `low`, `high` | numeric bounds in percent; `high` = 100 for open-ended ">X%" |
| `label` | the value as the speaker gave it |
| `scope` | what "doom" meant in context |
| `horizon` | time frame, if stated |
| `quote` | exact words, when available |
| `source_url`, `source_type` | where to hear or read it |
| `date` | ISO date of the statement (X posts: derived from the tweet ID) |
| `verified` | re-checked against the primary source by a maintainer |
| `tags` | `lab`, `ex-lab`, `researcher`, `safety`, `academic`, `survey`, `forecaster`, `founder`, `investor`, `policy`, `writer`, `advocate`, `podcaster` |
| `note` | caveats the speaker attached |

## Contributing

Open an issue using the **New estimate** template, or send a pull request editing `pdoom.json`. Include the exact quote and a link where a stranger can confirm it. Submissions without a primary source are not merged.

## Citing

> The p(doom) database, pdoomcoin.lol, retrieved YYYY-MM-DD. CC-BY-4.0.

## Provenance

Seeded from PauseAI's p(doom) list (re-sourced) and the estimates on pdoomcoin.lol's board. Maintained by the p(doom) project. The coin is a memecoin; the data is not.
