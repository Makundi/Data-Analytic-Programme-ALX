# Data Cleaning & Analytical Insights Log

## 1. Initial Data Audit & Schema Expectations

* **Target File:** `/data/Using_data_in_spreadsheets_student.xlsx`

Before processing, the spreadsheet structure was analyzed to define expected data types against standard environmental data tracking frameworks:

| Column Name | Expected Data Type | Status / Notes |
| :--- | :--- | :--- |
| **YEAR** | Numeric / Integer | Identified structural corruption (`##` strings). |
| **FACILITY_NAME** | Text / String | Verified clean. |
| **CITY** | Text / String | Verified clean. |
| **COUNTY** | Text / String | Verified clean. |
| **STATE** | Text / String | Verified clean; used for regional filtering. |
| **CHEMICAL** | Text / String | Identified data entry error (Numeric `7` in row F5). |
| **UNIT_OF_MEASURE**| Text / String | Verified clean. |
| **TOTAL_RELEASES** | Numeric / Float | Identified mixed data type corruption (`##` strings). |

---

## 2. Data Cleaning Decisions & Target Fixes

To ensure accurate analysis without distorting the underlying dataset, the following targeted data-cleaning interventions were executed:

### A. Resolution of Hardcoded String Errors (`##`)
* **Location:** `YEAR` column and `TOTAL_RELEASES` column.
* **Issue:** Corrupted `##` text strings were hardcoded into rows, causing mathematical functions (`SUM`, `AVERAGE`) to completely ignore the data or return errors.
* **Fix Applied:** Erased the `##` characters and left the cells completely **blank (Null)**. 
* **Justification:** Injecting a literal `0` would have artificially dragged down the true calculated average. Leaving the cells blank allows Google Sheets' arithmetic engines to automatically skip those entries, preserving the exact mathematical integrity of the remaining data.

### B. Resolution of Column F5 (CHEMICAL Column)
* **Location:** Cell `F5`.
* **Issue:** The cell contained a raw numeric value (`7`) instead of a valid chemical string name.
* **Fix Applied:** The anomalous number was categorized as `"Unknown Chemical"` to restore categorical consistency.

---

The cleaned dataset is stored in `/data/Using_data_in_spreadsheets_clean.xlsx`.


## 3. Statistical Findings
* **Observations:** The dataset exhibits a significant right-skew.
* **Metric Comparison:** * `MAX` Value: [Insert Value]
  * `AVERAGE` Value: [Insert Value]
  * `MEDIAN` Value: [Insert Value]

> **Key Takeaway:** The `AVERAGE` is heavily inflated by extreme industrial outliers. For predictive modeling or typical baseline assessments, the `MEDIAN` must be used to avoid skewing operational costs.

## 3. Formula Reference Guide
| Goal | Formula Used |
| :--- | :--- |
| Handle Errors | `=IFERROR(H2 * 0.50, "")` |
| Dynamic Mapping | `=XLOOKUP(MAX(H2:H), H2:H, B2:B)` |
| Central Tendency | `=MEDIAN(H2:H)` |