# Nobel Laureates DataFrame

A small Python project that retrieves Nobel laureate data from the official Nobel Prize API, reshapes it into a pandas DataFrame, and saves the result as a CSV file.

Each row represents one laureate and one prize. If a laureate received more than one prize, each prize appears on a separate row.

## Project files

- `nobel_api_to_dataframe.py` — downloads the API data, builds the DataFrame, and writes the CSV.
- `nobel_laureates_dataframe.csv` — generated dataset snapshot.

## Requirements

- Python 3.10 or newer
- pandas
- Internet access to retrieve data from the API

Install pandas with:

```bash
python -m pip install pandas
```

## Run the project

From the project folder, run:

```bash
python nobel_api_to_dataframe.py
```

The script fetches laureates in pages from the API, expands each laureate's prize list into separate rows, and creates `nobel_laureates_dataframe.csv` in the current folder.

To load the CSV into pandas:

```python
import pandas as pd

df = pd.read_csv("nobel_laureates_dataframe.csv")
print(df.head())
```

## Data columns

| Column | Description |
|---|---|
| `id` | Nobel API ID for the laureate. |
| `fullName` | Laureate's full name in English; blank for organizations. |
| `orgName` | Organization name in English; blank for individual laureates. |
| `gender` | Gender value provided by the API; blank for organizations or when unavailable. |
| `birth_date` | Birth date provided by the API. |
| `now_country` | Current English name for the country associated with the laureate's birthplace in the API. This is not necessarily the laureate's citizenship or present residence. |
| `death_date` | Date of death when recorded; otherwise blank. |
| `prize` | Full English name of the prize category. |
| `award_year` | Year the prize was awarded. |

Blank fields mean the API does not provide that value for the laureate. Organization entries, for example, generally have no personal name, gender, or birth and death dates.

## Data snapshot

The included CSV was generated from the API on 15 October 2026. That snapshot contains 1,028 laureate records expanded into 1,036 laureate–prize rows, covering award years 1901–2026. These totals can change when the Nobel Prize API is updated; rerun the script to refresh the dataset.

## Data source and terms

Data is retrieved from the [Nobel Prize API v2.1](https://api.nobelprize.org/2.1/laureates). The Nobel Prize developer information describes the API as open data and directs users to its [terms of use](https://www.nobelprize.org/about/terms-of-use-for-api-nobelprize-org-and-data-nobelprize-org/), which state that the service data is available under Creative Commons Zero (CC0).

## License

The Nobel Prize API terms identify the API data as CC0. This repository does not declare a separate license for its Python code; add a code license if you want others to reuse it under specific terms.
