# Businesses

`businesses.csv` maps a cleaned business name to a NAICS code. The money app turns the code into one of its spending categories.

| Column | Meaning |
| --- | --- |
| `name` | Business name, lowercased and cleaned (store numbers and punctuation removed). One row per name. |
| `naics` | The most specific NAICS code seen for that name (the most digits). The number of rows only breaks a tie. 2 to 6 digits. |

- Rows: 279,847
- SHA-256: `93366f9ebe1ea0e7f7a48125554e89fc03c45fd9c96b71ed397ed018a6543e54`
- Made from: Open Database of Businesses, version 1.0 (ODBus_v1.csv, 446,574 rows)
- Made by: `crates/core/examples/dedupe_businesses.rs` in the money app repo. A plain script, no model.
- Names with no NAICS code in the source (64,294 rows) are left out.
- Number of locations is not kept. A name seen many times appears once.

## Licence and source

Contains information licensed under the [Open Government Licence – Canada](https://open.canada.ca/en/open-government-licence-canada). Source: Statistics Canada, Open Database of Businesses.

This is open data about businesses. It is not financial advice.

## Review list

`review.csv` lists the 893 names that appear on more than 10 rows in the source, biggest first. Columns: `name`, `rows`, `naics` (the code chosen) and `codes_seen` (up to five `code:rows` pairs). Use it to check the chains that matter most. Some entries are generic, for example numbered companies such as `bc ltd`.
