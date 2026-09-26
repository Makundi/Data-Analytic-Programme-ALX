# Module 1: Preparing Data for Analysis

This folder contains core exercises focused on **Data Cleaning, Structural Normalization, and Exploratory Data Analysis (EDA)** using spreadsheet techniques. Accurate data analytics relies heavily on human verification to catch structural anomalies, handle data corruption, and challenge baseline assumptions before passing insights.

---

### 📂 Module Folder & Resources
All raw datasets, data dictionaries, and processed files for this module are stored in the local subfolder:
👉 **[Browse Module 1 Directory](./Preparing_Data_For_Analysis/)**

| Asset / File | Description | Link |
| :--- | :--- | :--- |
| **Data Folder** | Primary directory for Module 1 exercises | [`/Preparing_Data_For_Analysis/Data`](./Preparing_Data_For_Analysis/) |
| **Raw Dataset** | Uncleaned baseline dataset used for EDA | [`raw_data.xlsx`](./Preparing_Data_For_Analysis/Data/Using_data_in_spreadsheets_student.xlsx) |
| **Cleaned Dataset** | Final normalized and validated data | [`cleaned_data.xlsx`](./Preparing_Data_For_Analysis/Data/Using_data_in_spreadsheets_clean.xlsx) |
| **Google Sheet** | Interactive cloud version with formulas | [View Live Sheet ↗](https://docs.google.com/spreadsheets/d/1sXOFahQUdCh37vfwyvQJCK2ChZWkYDzLxr6cYMguSiM/edit?usp=sharing) |

---

# Module 2: Descriptive Analysis and Visualization

This section covers summarizing datasets using descriptive statistics to evaluate central tendencies, variability, and data distribution patterns directly within spreadsheets.

### 🔗 Project Links & Worksheets
* 📊 [Descriptive Statistics](https://docs.google.com/spreadsheets/d/1Pk68g2F2dsamVBfWOWqr1m-xztSyekPK/edit?usp=sharing&ouid=115371234275515848882&rtpof=true&sd=true)


## 1. Measures of Central Tendency
Identifies a single value that describes the typical center of a dataset:
* **Mean:** Calculates the arithmetic average of all values ($\text{Mean} = \frac{\text{Sum of all data points}}{n}$). Most appropriate when data contains no extreme outliers.
  * *Spreadsheet Formula:* `=AVERAGE(value1, [value2, ...])`
* **Median:** Represents the exact middle value after ordering data sequentially. Preferred measure when dealing with heavily skewed data or outliers.
  * *Spreadsheet Formula:* `=MEDIAN(value1, [value2, ...])`
* **Mode:** Identifies the value that occurs most frequently. Used primarily for categorical data containing fixed groups.
  * *Spreadsheet Formula:* `=MODE(value1, [value2, ...])`
* **Quartiles:** Segments a dataset's ordered distribution into four equal quarters, where $Q2$ represents the median.
  * *Spreadsheet Formula:* `=QUARTILE(data, quartile_number)`

---

## 2. Measures of Spread
Describes how spread out or dispersed data points are relative to each other and the center:

| Metric | Description | Formula / Logic | Spreadsheet Formula |
| :--- | :--- | :--- | :--- |
| **Range** | Total spread between extreme values. | $\text{Max} - \text{Min}$ | `=MAX(...) - MIN(...)` |
| **Interquartile Range (IQR)** | Evaluates the variability of the middle 50% of the dataset. | $Q3 - Q1$ | `=QUARTILE(data, 3) - QUARTILE(data, 1)` |
| **Variance** | Average squared distance from the mean. | $\sigma^2 = \frac{\sum (x - \text{mean})^2}{n}$ | `=VAR(value1, [value2, ...])` |
| **Standard Deviation** | Average amount of dispersion relative to the mean. | $\sigma = \sqrt{\frac{\sum (x - \text{mean})^2}{n}}$ | `=STDEV(value1, [value2, ...])` |

---

## 3. Key Analytical Takeaways
* **Choosing the Right Landmark:** Reporting median instead of mean to prevent skewed interpretations when outliers are present.
* **Evaluating Consistency:** Combining measures of central tendency with standard deviation and IQR to evaluate how reliably the mean or median represents the underlying data distribution.

---

## 2. Data Visualization & Chart Selection

Choosing the correct visualization begins by answering one core question: **"What would you like to show?"** Chart selection is organized into four main categories:

                 ┌───────────────────────────┐
                 │ What would you like to    │
                 │          show?            │
                 └─────────────┬─────────────┘
      ┌────────────────┬───────┴───────┬────────────────┐
      ▼                ▼               ▼                ▼
Comparison       Relationship     Distribution     Composition

### 📊 Comparison
Used to compare values across items or track trends over time.
* **Among Items:**
  * *Few Categories (1 variable/item):* Horizontal or Vertical Bar Chart.
  * *Many Categories:* Table or tables with embedded charts.
  * *Two Variables per Item:* Variable width bar chart.
* **Over Time:**
  * *Cyclical Data:* Circular area chart.
  * *Non-Cyclical Data (Many periods):* Line chart.
  * *Single or Few Categories (Few periods):* Vertical Bar Chart or Line Chart.

### 📈 Relationship
Used to show connections, correlations, or interactions between variables.
* **Two Variables:** Scatter plot.
* **Three or More Variables:** Bubble chart.

### 📉 Distribution
Used to illustrate how individual data points are spread across continuous or discrete ranges.
* **One Variable (Few data points):** Bar histogram.
* **One Variable (Many data points):** Line histogram.
* **Two Variables:** Scatter plot.

### 🧩 Composition
Used to display how individual parts make up a whole, either statically or dynamically over time.
* **Static:**
  * *Simple Share of Total:* Pie chart.
  * *Accumulation or Subtraction to Total:* Waterfall chart.
  * *Components of Components:* Stacked 100% bar chart with subcomponents.
  * *Accumulation to Total & Absolute Difference:* Tree map.
* **Changing Over Time:**
  * *Few Periods (Relative differences only):* Stacked 100% bar chart.
  * *Few Periods (Relative & absolute differences):* Stacked bar chart.
  * *Many Periods (Relative differences only):* Stacked 100% area chart.
  * *Many Periods (Relative & absolute differences):* Stacked area chart.

---

## 3. Core Analytical Takeaways
* **Avoiding Skewed Interpretations:** Knowing to report the median and IQR instead of the mean when data contains severe outliers.
* **Assessing Data Reliability:** Combining central tendency with standard deviation to determine how closely individual data points cluster around the average.
* **Purpose-Driven Charting:** Selecting chart types based on category counts, period density, and the core analytical goal (Comparison, Relationship, Distribution, or Composition) to prevent misleading stakeholders.