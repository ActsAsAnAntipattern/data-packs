# Businesses

`businesses.csv` maps a cleaned business name to a NAICS code. The money app turns the code into one of its spending categories.

| Column | Meaning |
| --- | --- |
| `name` | Business name, lowercased and cleaned (store numbers and punctuation removed). One row per name. |
| `naics` | The most common NAICS code for that name. 2 to 6 digits. |

- Rows: 279,847
- SHA-256: `eac21cf30af4eab0afdffb094cdc7a452423986a6daa27638a772aa040f793f8`
- Made from: Open Database of Businesses, version 1.0 (ODBus_v1.csv, 446,574 rows)
- Made by: `crates/core/examples/dedupe_businesses.rs` in the money app repo. A plain script, no model.
- Names with no NAICS code in the source (64,294 rows) are left out.
- Number of locations is not kept. A name seen many times appears once.

## Licence and source

Contains information licensed under the [Open Government Licence – Canada](https://open.canada.ca/en/open-government-licence-canada). Source: Statistics Canada, Open Database of Businesses.

This is open data about businesses. It is not financial advice.
