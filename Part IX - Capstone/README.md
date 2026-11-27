# Online Retail — End-to-End Exploratory Data Analysis

## Project Overview

This project presents an end-to-end Exploratory Data Analysis (EDA) of the Online Retail dataset.

The objective is to investigate transaction patterns, assess data quality, prepare a defensible analytical population, identify meaningful patterns, and communicate findings through statistical analysis and visualizations.

The analysis uses Python and its data analysis ecosystem, including Pandas, NumPy, Matplotlib, Seaborn, and SciPy.

## Dataset

**Source:** [UCI Machine Learning Repository — Online Retail](https://archive.ics.uci.edu/dataset/352/online+retail)

**DOI:** https://doi.org/10.24432/C5BW33

**Original dataset characteristics:**
- 541,909 transaction-line records
- 8 original variables
- 38 countries
- Transaction period: December 1, 2010 – December 9, 2011

The dataset contains transactional records from a UK-based online retail business.

The observational unit is an invoice line item.

### Original Variables

| Variable    | Description               |
| ----------- | ------------------------- |
| InvoiceNo   | Invoice identifier        |
| StockCode   | Product identifier        |
| Description | Product description       |
| Quantity    | Number of units purchased |
| InvoiceDate | Transaction date and time |
| UnitPrice   | Unit price                |
| CustomerID  | Customer identifier       |
| Country     | Customer's country        |

## Project Structure

```text
Part IX - Capstone/
│
├── config/
│   └── config.toml
│
├── data/
│   ├── interim/
│   ├── processed/
│   └── raw/
│
├── logs/
│
├── notebooks/
│   └── End_to_End_EDA.ipynb
│
├── outputs/
│   ├── profiling/
│   └── tables/
│
├── reports/
│   └── figures/
│
├── src/
│   ├── data_loading.py
│   ├── data_quality.py
│   └── eda_utils.py
│
├── .gitignore
├── pyproject.toml
├── uv.lock
└── README.md
```

## Methodology

The analysis follows a structured EDA workflow.

### 1. Data Understanding
- Dataset structure and dimensions
- Variable types and observational unit
- Initial descriptive statistics

### 2. Data Quality Assessment
- Duplicate records
- Missing values and missingness patterns
- Numeric validity
- Unusual transaction values
- Operational and special stock codes
- Temporal and geographic characteristics

### 3. Data Preparation
- Feature engineering
- Transaction classification
- Analytical population evaluation
- Export and verification of prepared datasets

### 4. Exploratory Data Analysis
- Quantitative distributions
- Categorical distributions
- Geographic patterns
- Product activity
- Temporal patterns
- Relationships among quantitative variables

### 5. Findings and Recommendations
- Key analytical findings
- Data limitations
- Business-oriented recommendations
- Final conclusions

## Analytical Population

The original dataset contains 541,909 records.

Following data assessment and transaction classification, the project selected **527,948 positive-sales-candidate records**, representing approximately 97.42% of the original dataset.

The selected population includes records satisfying the following conditions:

- Positive quantity
- Positive unit price
- Numeric invoice identifier
- Not classified as an operational or non-merchandise code

These records are described as positive-sales candidates, not verified completed or paid sales.

CustomerID is missing for approximately 24.90% of the selected population. Records without customer identifiers are retained for analyses that do not require customer-level identification.

## Key Findings

### Geographic Distribution
- The United Kingdom accounts for approximately 91.69% of selected records.
- The five most active countries account for approximately 96.82%.

### Product Activity
- The selected population contains 3,917 distinct stock codes.
- Product rankings differ depending on record frequency, total quantity, and total line value.

### Quantitative Distributions
- Quantity, UnitPrice, and LineValue exhibit strong positive skewness and heavy tails.
- Extreme observations have a substantial influence on means and standard deviations.

### Temporal Patterns
- November 2011 recorded the highest monthly activity.
- Thursday recorded the highest weekday activity.
- Most transaction activity occurred between 9:00 and 16:00.

### Relationships
- Quantity and LineValue have a strong positive Pearson correlation of 0.916.
- Quantity and UnitPrice have a Pearson correlation of -0.022 and a Spearman correlation of -0.402.

These relationships are interpreted in the context of the mathematical definition of LineValue as Quantity multiplied by UnitPrice.

## Important Analytical Limitations

- The dataset represents historical transactions from 2010–2011.
- Missing customer identifiers limit customer-level analysis.
- Positive-sales candidates are not necessarily verified completed sales.
- Cancellation invoices cannot always be reliably linked to their original invoices.
- LineValue represents transaction line value, not verified accounting revenue.
- Statistical outliers are not automatically treated as errors.
- Observed associations do not establish causation.
- December 2011 is incomplete, ending on December 9.

## Technology Stack

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- SciPy
- OpenPyXL
- PyArrow
- Jupyter Notebook
- uv for Python dependency management

## Reproducibility

### Requirements

- Python version compatible with the project's `pyproject.toml`
- [uv](https://docs.astral.sh/uv/)

### Setup

Clone or download the project repository.

Place the original dataset in:

```text
data/raw/Online Retail.xlsx
```

Install the project dependencies using:

```bash
uv sync --locked
```

Activate the project environment:

**Windows CMD:**

```cmd
.venv\Scripts\activate.bat
```

Launch Jupyter:

```bash
uv run jupyter notebook
```

Open:

```text
notebooks/End_to_End_EDA.ipynb
```

Execute the notebook cells sequentially.

## Data Source and Attribution

Chen, D. (2015). *Online Retail* [Dataset]. UCI Machine Learning Repository.

https://doi.org/10.24432/C5BW33

The dataset is distributed under the Creative Commons Attribution 4.0 International (CC BY 4.0) license.

## Project Status

Analytical work and notebook validation completed.

Documentation and final report preparation are completed.