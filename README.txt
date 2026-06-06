# README


## 1. Project Overview
This project investigates whether the so‑called “Seven‑Year Itch” appears in real divorce patterns by analysing when marriages typically end across European countries. Using administrative population data from the United Nations Demographic Statistics Database, the analysis examines both cross‑sectional variation in peak divorce timing and long‑term trends in the distribution of divorces by duration of marriage. The study focuses on the 1995–2025 period, which represents the most recent 30 years, and applies a harmonised set of duration‑of‑marriage categories to enable comparability across countries.

## 2. Data Source

### 2.1 Data Description
- Dataset name: Divorces by duration of marriage
- Provider: United Nations Statistics Division (UNSD)
- Original source: UN Demographic Yearbook / Demographic Statistics Database
- Format: CSV
- Last updated: 26 February 2026
- Author of the processed data: Nattamon Wattanapenpaiboon (Monash University, as a part of ETC5512)

### 2.2 Temporal Coverage
- Full dataset: 1948–2025
- Analysis window: 1995–2025 (chosen as analytically meaningful period)

### 2.3 Spatial Coverage
- 105 reporting countries or areas (questionnaires sent to over 230 countries and areas)
- Analysis restricted to European countries due to consistent reporting

### 2.4 Data Type
Administrative population data derived from national civil registration systems. Although census‑style in that reporting countries provide complete counts of all recorded divorces, the global dataset is incomplete because some countries do not legally recognise divorce or do not submit divorce statistics to the UN Demographic Yearbook.

### 2.5 Licence / Terms of use
UNdata Terms of Use:
- Free reuse with attribution
- No endorsement
- No commercial misuse

### 2.6 Privacy / Ethics
- Fully aggregated data
- No personal identifiers
- No privacy risks

## 3. Key Limitations

### 3.1 Incomplete global coverage
Many countries do not submit divorce‑duration statistics to the UN, resulting in substantial geographic gaps. Europe provides the most complete and consistent divorce‑duration data, so the analysis focuses on European countries to ensure comparability and minimise bias introduced by missing or irregular data

### 3.2 Differences in duration‑of‑marriage categories
Countries use different binning schemes, requiring standardisation and sometimes forcing loss of detail.

### 3.3 Legal and institutional differences
Countries vary widely in divorce laws, waiting periods, and registration systems. Some report divorces by year of occurrence while others use year of registration, affecting comparability across countries.

### 3.4 Some countries report by year of occurrence vs year of registration
This creates timing inconsistencies, as divorces finalised in one year may be recorded in the next, making cross‑country comparisons of annual totals less precise.

### 3.5 Harmonisation required before analysis (described below)

## 4. Data Cleaning and Harmonisation
- initial cleaning and footnote removal
- constructing comparable percent-of-total measures
- restricting the analysis window (1995-2025)
- standardising duration-of-marriage categories*
- harmonising country names for mapping
- restricting the dataset to Europe**

### Key Data Processing Decisions

- Standardising duration-of-marriage categories*: Countries report duration‑of‑marriage categories using inconsistent formats, including single years, multi‑year ranges, open‑ended values (e.g., “10+”), and “Less than X” labels. To enable cross‑country comparison, I extracted all numeric values from each label and used the maximum value as the upper bound of the category. For “Less than X” labels, I assumed the category covers 0 to (X–1) years, as the UN does not specify the exact boundaries. These upper bounds were then collapsed into five global bins (0–1, 1–2, 3–4, 5–9, 10+). This approach standardises heterogeneous reporting but introduces limitations, including loss of granularity, potential misclassification of ambiguous labels, and uncertainty about how “Less than X” categories are defined across countries.

- Restricting the dataset to Europe**: Before analysis, data availability was assessed by identifying whether each country had any non‑missing divorce‑duration observations. This completeness indicator was joined to the world map and visualised. The map showed that Europe has the highest concentration of countries with available data, while many regions outside Europe have sparse or missing reporting. Given the substantial variation in completeness across regions, the final dataset was restricted to European countries. This decision ensures that the subsequent analysis is based on the region with the most complete and reliable reporting. Only relevant analytical columns were retained in the final dataset.

## 5. File Structure
ETC5512-assignment4
├── assignment4_template_Nattamon_Wattanapenapiboon.html  -> Rendered .qmd report as .html
├── assignment4_template_Nattamon_Wattanapenapiboon.qmd   -> .qmd file, including Data Download, Wrangling, Analysis, and Behind the Scenes
├── data
    ├──  UNdata_Export_20260528_021328529.csv     -> raw data of "Divorces by duration of marriage" provided by UNSD
    ├──  clean_europe_divorces_by_duration_of_marriage.csv       -> Processed data used in the analysis, see data dictionary for details
    ├──  data-dictionary.xlsx   -> Data dictionary providing detailed information about the dataset after processing
├── README.txt                  -> this file
└── Assignment4.Rproj
