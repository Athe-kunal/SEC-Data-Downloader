# SEC DATA DOWNLOADER
This repository downloads all the texts from SEC documents (10-K and 10-Q). Currently, it is not supporting documents that are amended, but that will be added in the near futures.

Install the required dependencies

```
python install -r requirements.txt
```

Inside the `data.yaml`, you can find the following default config

```
{
  tickers: ['TSLA','AAPL','GOOGL'],
  amount: 5,
  document_type: "10-K",
  num_workers: 5
}
```

This will download the 10-K documents for the last 5 years for the stocks `['TSLA','AAPL','GOOGL']`. The `num_workers` is for parallel processing and multi-threading. We have multi-threading at the ticker level and multi-processing at the year level for a given ticker

After changing the config in the `data.yaml` file, run the main file

```
python main.py
```

It will download the data in the following directories and sub-directories

```
- AAPL
  - 2018
    - 10-K.json
  - 2019
    - 10-K.json
  - 2020
    - 10-K.json
  - 2021
    - 10-K.json
    - 10-Q_12.json
  - 2022
    - 10-K.json
    - 10-Q_03.json
    - 10-Q_06.json
    - 10-Q_12.json
  - 2023
    - 10-Q_04.json
- GOOGL
  - 2018
    - 10-K.json
  - 2019
    - 10-K.json
  - 2020
    - 10-K.json
  - 2021
    - 10-K.json
    - 10-Q_09.json
  - 2022
    - 10-K.json
    - 10-Q_03.json
    - 10-Q_06.json
    - 10-Q_09.json
  - 2023
    - 10-Q_03.json
- TSLA
  - 2018
    - 10-K.json
  - 2019
    - 10-K.json
  - 2020
    - 10-K.json
  - 2021
    - 10-K.json
    - 10-Q_09.json
  - 2022
    - 10-K.json
    - 10-Q_03.json
    - 10-Q_06.json
    - 10-Q_09.json
  - 2023
    - 10-Q_03.json
```

Here for each ticker we have separate folders with 10-K data inside respective years and 10-Q data is saved in the respective year along with the month. `10-Q_03.json` means March data of 10-Q document.

## REFERENCES
1. Unstructured SEC Filings API: [repo link](https://github.com/Unstructured-IO/pipeline-sec-filings/tree/main)
2. SEC Edgar Downloader: [repo link](https://github.com/jadchaar/sec-edgar-downloader)