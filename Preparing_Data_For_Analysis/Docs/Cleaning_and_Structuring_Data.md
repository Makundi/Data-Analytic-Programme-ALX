# Data Cleaning Log: Delimiter Normalization

## 1. Problem Statement & Discovery
Briefly describe the raw state of the incoming files.
* **Target Files:** `Supply_chain_emission_factors_US_industries_commodities_student_version (1).csv`, `Streamflow_student_version.xlsx`
* **Anomalies Observed:** Mixed delimiters (`~`, `;`, `|`) running concurrently in identical attributes; adjacent duplicate delimiters (`;;`, `||`) throwing off the default CSV grid.

## 2. Processing Framework & Mechanics
Explain the exact logic applied to standardizing data objects. 

### Method A: Targeted Batched Splits
Used for isolated rows with singular variations (`~` or `|` processing batches).
* **Formula:** `=SPLIT(A2, "~")`
* **Action:** Split, copy, and apply `Paste Special > Paste Values Only` to decouple live data from row dependencies.

### Method B: Regular Expression Multi-Match
Used for multi-delimiter strings containing consecutive repetitions.
* **Formula:** `=SPLIT(REGEXREPLACE(C2, "[;|]+", ","), ",")`
* **Logic:** The `[;|]+` class targets any dynamic sequence of characters containing a semicolon or a pipe and normalizes the target string to a singular comma split anchor.

The cleaned dataset is stored in `/data/Cleaning_and_Structuring_Data_Clean.xlsx`.

## 3. Quality Assurance & Verification
Document the mathematical validation protocol used to guarantee data integrity.

* **Audit Query:**
  ```excel
  =IF(LEN(REGEXREPLACE(A2, "[;|]+", "|")) - LEN(REGEXREPLACE(A2, "[;|]+", "")) + 1 = COUNTA(B2:Z2), "Match", "Not a Match")