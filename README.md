# FDA Drug NDC Directory: 138,262 US drug products

[![Apify Actor](https://img.shields.io/badge/Apify-Actor-1f6feb)](https://apify.com/phonic_lily/fda-drug-ndc-directory) ![Licence](https://img.shields.io/badge/licence-CC0_1.0_Universal-blue) ![Records](https://img.shields.io/badge/records-138%2C569-green)

Search 138,262 US drug products from the FDA National Drug Code (NDC) Directory via openFDA: brand and generic name, labeler, dosage form, route, marketing category, DEA schedule, active ingredients with strength, pharmacologic class, UNII and RxCUI. Embedded data, no scraping, pay per record.

## What you get
- **138,569 records**, each carrying its own `license` and `attribution` fields, ready to republish with the required credit.
- A **100-record free sample** in this repository: [`sample.jsonl`](sample.jsonl) and [`sample.csv`](sample.csv) (opens as a table on GitHub).
- The **full dataset** as a filterable API (JSON, CSV, Excel), no scraping, no login: [FDA Drug NDC Directory: 138,262 US drug products on Apify](https://apify.com/phonic_lily/fda-drug-ndc-directory).

## One record
```json
{
  "product_id": "71335-2969_41dc54e5-b4d3-e7ae-e063-6294a90a31f0",
  "product_ndc": "71335-2969",
  "brand_name": "Hydrocodone Bitartrate and Acetaminophen",
  "generic_name": "Hydrocodone Bitartrate and Acetaminophen",
  "labeler_name": "Bryant Ranch Prepack",
  "product_type": "HUMAN PRESCRIPTION DRUG",
  "dosage_form": "TABLET",
  "route": "ORAL",
  "marketing_category": "ANDA",
  "application_number": "ANDA202214",
  "finished": true,
  "marketing_start_date": "2014-10-06"
}
```

## Quick start
Python:
```python
from apify_client import ApifyClient
client = ApifyClient('<YOUR_APIFY_TOKEN>')
run = client.actor('phonic_lily/fda-drug-ndc-directory').call(run_input={'maxResults': 10})
for item in client.dataset(run['defaultDatasetId']).iterate_items():
    print(item)
```
Or from the command line:
```bash
curl -X POST 'https://api.apify.com/v2/acts/phonic_lily~fda-drug-ndc-directory/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>' \
  -H 'Content-Type: application/json' -d '{"maxResults": 10}'
```
Pricing is pay-per-record on Apify (see the Actor page); the sample here is free.

## Fields
| Field | Description |
|---|---|
| `product_id` | Stable openFDA product identifier (product NDC plus SPL id). |
| `product_ndc` | Product NDC (labeler-product code). |
| `brand_name` | Brand (proprietary) name, null if none. |
| `generic_name` | Generic (non-proprietary) name. |
| `labeler_name` | Company that labels the product. |
| `product_type` | Product type (human prescription, OTC, vaccine, bulk ingredient...). |
| `dosage_form` | Dosage form. |
| `route` | Administration routes, '; '-joined. |
| `marketing_category` | Marketing category (NDA, ANDA, BLA, unapproved...). |
| `application_number` | FDA application number, null if none. |
| `finished` | True for a finished drug product, false for bulk or further-processing material. |
| `marketing_start_date` | Marketing start date, YYYY-MM-DD. |
| `marketing_end_date` | Marketing end date, YYYY-MM-DD, null if still marketed. |
| `listing_expiration_date` | NDC listing expiration date, YYYY-MM-DD. |
| `dea_schedule` | DEA controlled-substance schedule, null if not scheduled. |
| `active_ingredients` | Active ingredients with strength, '; '-joined. |
| `active_ingredient_count` | Number of active ingredients. |
| `pharm_class` | Pharmacologic classes (MoA, EPC...), '; '-joined. |
| `package_count` | Number of packages listed for the product. |
| `package_descriptions` | First five package descriptions, ' / '-joined. |
| `unii` | UNII codes of ingredients, '; '-joined. |
| `rxcui` | RxNorm concept ids, '; '-joined. |

## Data, licence and attribution
openFDA drug/ndc bulk export (https://api.fda.gov/download.json, last updated 2026-11-06). openFDA content is public domain under a Creative Commons CC0 1.0 Universal dedication (https://open.fda.gov/terms/): reuse, including commercial, needs no permission. One record per NDC product (product_id). Dates are ISO YYYY-MM-DD. Null means the source gives no value; it is never 0 or empty. Multi-valued fields (route, ingredients, pharmacologic classes, UNII, RxCUI) are joined with '; '. Package details are summarised (count and first five descriptions). Do not rely on this data to make decisions regarding medical care.

**Licence:** CC0 1.0 Universal (public domain), U.S. Food and Drug Administration via openFDA

**Attribution:** Source: U.S. Food and Drug Administration, National Drug Code Directory via openFDA (https://open.fda.gov/), data dated 2026-11-06. CC0 1.0 Universal per https://open.fda.gov/terms/. FDA does not endorse this product; do not rely on this data for medical decisions.

Snapshot date: 2026-11-22. Empty values are `null`, never 0.

## Cite this dataset
GitHub's *Cite this repository* button reads [`CITATION.cff`](CITATION.cff).

## Feedback
Found an error or want a field added? Open an issue in this repository.
