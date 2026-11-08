# Businesses

`businesses.sqlite` is a data pack for the money app. It maps a cleaned business name to a NAICS code. The app turns the code into one of its spending categories.

Install it with the app (the app never downloads anything by itself):

```
curl -L -O https://raw.githubusercontent.com/ActsAsAnAntipattern/data-packs/main/businesses/businesses.sqlite
money data install businesses.sqlite
```

A newer version replaces the one you have, and keeps the old one so `money data undo businesses` can bring it back.

## What is inside

A SQLite file with two tables:

- `manifest`: format, pack, version, source, licence, rows, sha256
- `raw_data`: one row, `businesses.csv`, with the raw CSV text (`name,naics`)

| Column | Meaning |
| --- | --- |
| `name` | Business name, lowercased and cleaned (store numbers and punctuation removed). One row per name. |
| `naics` | The most specific NAICS code seen for that name (the most digits). The number of rows only breaks a tie. 2 to 6 digits. |

- Version: 2026.2 (2026.1 had junk names such as `0.1` and `bc ltd`)
- Rows: 279,272
- File SHA-256: `9b72207ff2a8e6c96f02768c17d1a11b7db8d86a8d81c996d87d9e32b54cbc9c`
- Contents SHA-256 (the CSV text, also in the manifest): `8ae7b84a54b16b82f1694e60983cd4165fe60702076f1378fbda272fb93964f2`
- Made from: Open Database of Businesses, version 1.0 (ODBus_v1.csv, 446,574 rows)
- Made by: `crates/core/examples/dedupe_businesses.rs` in the money app repo. A plain script, no model.
- Rows with no usable NAICS code (64,421) are left out. Codes that are not 2 to 6 digits are ignored. Junk names are dropped (472 names, 3,213 rows): names with no real word once legal endings (ltd, inc), province codes, "canada" and "the" are taken out, and initials with 10 locations or fewer.
- Number of locations is not kept. A name seen many times appears once.

## Review list

`review.csv` lists the 884 names that appear on more than 10 rows in the source, biggest first. Columns: `name`, `rows`, `naics` (the code chosen) and `codes_seen` (up to five `code:rows` pairs). Use it to check the chains that matter most.

`dropped.csv` lists the 9 junk names on more than 10 rows that were left out (for example `bc ltd`, 2,264 rows), so you can check nothing real was dropped. Columns: `name`, `rows`.

## Licence and source

Contains information licensed under the [Open Government Licence – Canada](https://open.canada.ca/en/open-government-licence-canada). Source: Statistics Canada, Open Database of Businesses.

This is open data about businesses. It is not financial advice.
