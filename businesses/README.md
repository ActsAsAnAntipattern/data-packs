# Businesses

`businesses.sqlite` is a data pack for the money app. It maps a cleaned business name to a NAICS code. The app turns the code into one of its spending categories.

Install it with the app (the app never downloads anything by itself):

```
money data install businesses.sqlite
```

## What is inside

A SQLite file with two tables:

- `manifest`: format, pack, version, source, licence, rows, sha256
- `raw_data`: one row, `businesses.csv`, with the raw CSV text (`name,naics`)

| Column | Meaning |
| --- | --- |
| `name` | Business name, lowercased and cleaned (store numbers and punctuation removed). One row per name. |
| `naics` | The most specific NAICS code seen for that name (the most digits). The number of rows only breaks a tie. 2 to 6 digits. |

- Version: 2026.1
- Rows: 279,744
- File SHA-256: `ddf6a5f50e880de0c5d8e7dc958b47ab73a02de85c905c1f9c7f14c2ae8901b0`
- Contents SHA-256 (the CSV text, also in the manifest): `10f30434d25c4a67dbe3285072366e0242bd4965ab3230f20d3554f43732911f`
- Made from: Open Database of Businesses, version 1.0 (ODBus_v1.csv, 446,574 rows)
- Made by: `crates/core/examples/dedupe_businesses.rs` in the money app repo. A plain script, no model.
- Rows with no usable NAICS code (64,421) are left out. Codes that are not 2 to 6 digits are ignored.
- Number of locations is not kept. A name seen many times appears once.

## Review list

`review.csv` lists the 893 names that appear on more than 10 rows in the source, biggest first. Columns: `name`, `rows`, `naics` (the code chosen) and `codes_seen` (up to five `code:rows` pairs). Use it to check the chains that matter most. Some entries are generic, for example numbered companies such as `bc ltd`.

## Licence and source

Contains information licensed under the [Open Government Licence – Canada](https://open.canada.ca/en/open-government-licence-canada). Source: Statistics Canada, Open Database of Businesses.

This is open data about businesses. It is not financial advice.
