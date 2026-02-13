# SEC Parsers

This directory contains parsing tools specifically designed to extract key sections from **US SEC 10-K Filings** using the `sec-parsers` and `sec-edgar-downloader` libraries.

##  Notebooks

### 1. `ITEM_1A_PARSER.ipynb` (Risk Factors)
- **Objective**: Extracts **Item 1A: Risk Factors** from 10-K filings.
- **Output**: Returns the raw text of the risk factors section, which is critical for the analysis performed in the `RISK ANALYSIS` folder.
- **Process**:
  - Downloads 10-K filings for specified tickers.
  - Parses the HTML/XML structure to locate "Item 1A".
  - Saves extracted text to CSV.

### 2. `SECTION 7 (MD&A) PARSER.ipynb` (Management's Discussion & Analysis)
- **Objective**: Extracts **Item 7: Management's Discussion and Analysis (MD&A)**.
- **Significance**: This section contains management's perspective on financial results, liquidity, and future outlook—key for sentiment analysis.
- **Features**:
  - **`process_filings_and_extract_mda`**: Downloads filings and extracts MD&A into individual CSVs (e.g., `TICKER_YEAR_section_7_mda.csv`).
  - **`sort_data_year_wise_combined`**: Aggregates extracted MD&A sections from all companies into a single CSV per year (e.g., `2023.csv`).
  - **Visualization**: Includes code to plot the number of companies processed per year.

##  Setup & Usage

### Dependencies
These notebooks rely on the following Python libraries:
```bash
pip install sec-parsers sec-edgar-downloader pandas matplotlib
```

### Configuration
**Crucial Step**: You must configure the `Downloader` with a valid User Agent (Entity Name and Email) as per SEC EDGAR pricing guidelines.

```python
from sec_edgar_downloader import Downloader
# Replace with your details
edgar_downloader = Downloader("MyCompanyName", "my.email@domain.com")
```

### Workflow
1.  **Define Tickers**: Update the list of tickers (e.g., S&P 500 list) in the `__main__` block.
2.  **Set Years**: Define the `start_year` and `end_year` for extraction.
3.  **Run Extraction**: Execute the cells to download and parse the data.
4.  **Output**: Check the generated `section_7_mda_results` (or similar) folder for CSV files.

## Important Notes
- **US Market Focus**: These parsers are strictly for **US Companies** filing with the SEC. They will **not work** for Indian companies or other non-US exchanges.
- **Rate Limiting**: The SEC imposes rate limits (currently < 10 requests/second). The `sec-edgar-downloader` handles this, but large bulk downloads may take time.
