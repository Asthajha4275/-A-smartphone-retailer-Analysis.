# Smartphone Market Performance Analysis – Saap (Python + Tableau)

A two-stage analytics project for **Saap**, a smartphone retailer. Stage 1 uses Python for data validation, exploratory analysis and hypothesis testing. Stage 2 uses Tableau for interactive dashboards and a data story. Stage 3 packages the work as a business report and presentation.

**Tools:** Python (Pandas, NumPy, Matplotlib, Seaborn, SciPy, Statsmodels) · Jupyter / Google Colab · Tableau Public Desktop · PowerPoint

---

## 1. Business Problem

Saap holds historical smartphone sales and customer data but lacks structured insight into what drives purchases. The goal is to run a statistical and visual analysis to understand:

- How price, specifications (RAM, battery, camera, performance) and operating system relate to each other
- How demographics (age, gender, salary, occupation, region) relate to brand and OS choice
- Which brands and features perform best, to support pricing, marketing and product-positioning decisions

---

## 2. Dataset

| Item | Detail |
|---|---|
| File | `cellphone_data.csv` |
| Size | 990 rows × 22 columns |
| Customer variables | user_id, gender, age, occupation, salary (INR), region (city), rating |
| Product variables | cellphone_id, brand, model, operating system, internal memory, RAM, performance score, main camera, selfie camera, battery size, screen size, weight, price (INR), release date |

---

## 3. Project Steps

### Stage 1 – Python Statistical Analysis (`Astha.ipynb`)

**Step 1 – Setup and load data**
Imported Pandas, NumPy, SciPy, Matplotlib and Seaborn, loaded the CSV and previewed its shape and first rows.

**Step 2 – Data preprocessing**
- Checked data types with `info()` / `describe()`
- Checked for missing values and duplicate records
- Trimmed whitespace in text columns (brand, model, OS, city) to avoid duplicate categories
- Converted release date to datetime and derived release year and month
- Flagged out-of-range values (e.g. very large RAM, very small battery)

**Step 3 – Split variables**
Separated numerical and categorical columns, excluding ID-like fields (user_id, cellphone_id) from numeric analysis.

**Step 4 – Exploratory data analysis**
- **Boxplots** for outliers in numeric variables
- **Correlation heatmap** among numeric variables (price, RAM, memory, cameras, battery, performance)
- **Count plots** for brand, OS, occupation, gender and region
- **Pair plots** for relationships between numeric variables
- Price comparison by OS (mean and median)

**Step 5 – Hypothesis testing (α = 0.05)**

| Test | Question | Result |
|---|---|---|
| Two-sample t-test | Salary difference by gender | Significant (p ≈ 0.025) |
| Two-sample t-test | Price: Android vs iOS | Significant (p < 0.001); iOS mean ≈ ₹64,206 vs Android ≈ ₹50,329 |
| One-sample t-tests | RAM > 16 GB, main camera > 12 MP, selfie camera > 8 MP, battery > 4000 mAh | Run against benchmark values (RAM > 16 GB not supported, p = 1.0) |
| Two-sample t-test | Salary: Delhi vs Mumbai | Run (see notebook) |
| ANOVA | Price across brands | Significant (F ≈ 105.7, p ≈ 0) |
| ANOVA | Price across occupations | Not significant (p ≈ 0.70) |
| ANOVA | Performance across age groups (<30, 30–50, >50) | Not significant (p ≈ 0.79) |
| ANOVA | Battery and main camera across brands; screen size and RAM across OS | Run (see notebook) |
| Chi-square | OS vs gender | Not significant (p ≈ 0.98) |
| Chi-square | Brand vs OS | Significant (p ≈ 0); expected, since each brand largely runs one OS |
| Chi-square | Brand vs occupation | Not significant (p ≈ 1.0) |

Each test includes a null/alternative hypothesis and a plain-language interpretation.

### Stage 2 – Tableau Dashboards and Story (`Astha Kumari Jha .twbx`)

**Step 6 – Load data into Tableau** from `cellphone_data.csv` and set correct data types.

**Step 7 – Build worksheets**, each answering one question:

1. KPI overview
2. Box plot of price by brand
3. Average rating by brand
4. Performance by brand
5. RAM vs performance score
6. Internal memory vs price
7. Camera-to-price ratio
8. Price segment vs camera score
9. Battery efficiency by brand
10. Gender-wise brand preference
11. Region-wise brand rating
12. Salary-wise affordability
13. Year-wise performance

**Step 8 – Assemble the dashboard / story** ("Cell Phone Insights Story"), moving from the KPI overview to deeper analysis and conclusions, with captions on each story point.

### Stage 3 – Report and Presentation

**Step 9 – Business report** (`Report (DSA) 1.pdf`): introduction, objectives, methodology, conclusion and recommendations.
**Step 10 – Presentation** (`last STAGE 3 PPT.pptx`): 15 slides summarising the problem, data, preprocessing, statistical findings, Tableau insights, conclusion and future work.

---

## 4. Key Findings

- **iOS phones are priced higher** than Android (mean ≈ ₹64.2K vs ≈ ₹50.3K), and the difference is statistically significant.
- **Brand drives price**: prices differ significantly across brands, showing clear budget and premium segments.
- **Android dominates** the sample at about 83% of records, with Apple the main premium alternative.
- **Higher specs go with higher prices** (RAM, camera, performance), supporting feature-driven pricing.
- **OS choice is not linked to gender**, and price does not differ significantly by occupation; performance ratings do not differ significantly by age group.
- **Salary differs significantly by gender** in this sample.

---

## 5. Recommendations

1. **Tiered pricing:** segment the range into budget, mid-range and premium, and benchmark Android vs iOS regularly.
2. **Feature-led marketing:** emphasise camera, RAM and battery, which tie most closely to price and ratings.
3. **Regional strategy:** adjust pricing and stock to regional demand and purchasing power.
4. **Product positioning:** place high-performance devices in the premium tier and sell mid-range models on value for money.
5. **Next steps:** apply proper data treatment, build predictive models for price and demand, add time-series analysis, and enrich the data with reviews and after-sales information.

---

## 6. Repository Structure

```
├── Astha.ipynb                      # Stage 1: Python EDA and statistical tests
├── Astha Kumari Jha .twbx           # Stage 2: Tableau workbook (worksheets + story)
├── Report (DSA) 1.pdf               # Business report
├── last STAGE 3 PPT.pptx            # Final presentation
├── cellphone_data.csv               # Dataset
└── README.md
```

## 7. How to Run

1. **Notebook:** open `Astha.ipynb` in Jupyter or Google Colab, upload `cellphone_data.csv` when prompted, and run all cells in order.
2. **Tableau:** open the `.twbx` in Tableau Public / Desktop and explore the worksheets and story.

## 8. Skills Demonstrated

Data cleaning · EDA · Hypothesis testing (t-test, ANOVA, Chi-square) · Tableau dashboards and storytelling · Business reporting

---

