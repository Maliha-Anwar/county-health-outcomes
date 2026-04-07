# County-Level Socioeconomic Determinants of Health Outcomes

An exploratory analysis of how county-level socioeconomic factors — median income, uninsurance rate, education, unemployment — predict health outcomes like premature mortality and diabetes prevalence across ~3,000 U.S. counties.

Built as a portfolio project demonstrating end-to-end data analysis in R: data wrangling, exploratory visualization, regression modeling, and an interactive Shiny dashboard.

---

## Research Question

**How do socioeconomic conditions at the county level predict premature mortality and chronic disease prevalence in the United States?**

This project examines the relationship between structural factors (income, insurance coverage, education, employment) and health outcomes using publicly available county-level data. The analysis uses multiple linear regression to estimate the independent contribution of each predictor while controlling for the others.

---

## Key Findings

> *[Update this section after completing your analysis. Include 2–3 key takeaways with specific numbers, e.g.:]*

- Counties in the lowest income quartile had premature death rates X times higher than the highest quartile.
- A 1 percentage-point increase in uninsurance was associated with an estimated Y additional years of potential life lost per 100,000, after adjusting for income, education, and unemployment.
- The model explained approximately Z% of the variation in premature mortality across counties (adjusted R² = 0.XX).

### Sample Visualizations

> *[After generating your plots, save them to `output/figures/` and embed them here:]*

```
![Scatter: Income vs. Premature Death](output/figures/scatter_income_mortality.png)
![Choropleth: Premature Mortality by County](output/figures/choropleth_ypll.png)
```

---

## Data Sources

| Dataset | Source | Year | Access |
|---------|--------|------|--------|
| County Health Rankings Analytic Data | [CHR&R (U. of Wisconsin / RWJF)](https://www.countyhealthrankings.org/health-data/methodology-and-sources/data-documentation) | 2025 | CSV download |
| County Shapefiles | U.S. Census Bureau via `tigris` R package | 2022 | Loaded in R |

**Note:** The raw data file is not included in this repository due to size. See [Reproducing This Analysis](#reproducing-this-analysis) below for download instructions.

### Variables Used

| Variable | CHR Code | Description |
|----------|----------|-------------|
| `premature_death` | v001 | Years of Potential Life Lost per 100,000 |
| `diabetes_pct` | v060 | Diabetes prevalence (%) |
| `uninsured_pct` | v085 | Uninsured population (%) |
| `median_income` | v063 | Median household income ($) |
| `pct_college` | v069 | Some college education (%) |
| `pct_unemployed` | v023 | Unemployment rate (%) |
| `adult_smoking` | v009 | Adult smoking prevalence (%) |
| `adult_obesity` | v011 | Adult obesity prevalence (%) |

---

## Project Structure

```
county-health-outcomes/
├── data/
│   ├── raw/                        # Original downloaded files (not tracked)
│   └── processed/
│       └── health_clean.csv        # Cleaned dataset
├── scripts/
│   ├── 00_download_data.R          # Downloads source data
│   ├── 01_data_import_and_clean.R  # Import, select, clean
│   ├── 02_eda.R                    # Exploratory analysis & plots
│   ├── 03_modeling.R               # Regression & diagnostics
│   └── 04_visualization.R          # Choropleth & polished figures
├── output/
│   ├── figures/                    # Saved plots (.png)
│   └── tables/                     # Model output tables
├── app.R                           # Shiny dashboard
├── .gitignore
├── health_outcomes.Rproj
└── README.md
```

---

## Reproducing This Analysis

### Prerequisites

- **R** (≥ 4.3) and **RStudio** (recommended)
- The following R packages:

```r
install.packages(c(
  "tidyverse", "janitor", "skimr", "corrplot",
  "broom", "gtsummary", "sf", "patchwork", "here",
  "shiny", "bslib", "plotly", "DT"
))
```

### Steps

1. **Clone this repository:**
   ```bash
   git clone https://github.com/YOUR-USERNAME/county-health-outcomes.git
   ```

2. **Open the `.Rproj` file** in RStudio.

3. **Download the data** — run the download script, or do it manually:
   ```r
   source("scripts/00_download_data.R")
   ```
   This downloads the 2025 CHR CSV Analytic Data from [countyhealthrankings.org](https://www.countyhealthrankings.org/health-data/methodology-and-sources/data-documentation) into `data/raw/`.

4. **Run the analysis scripts in order:**
   ```r
   source("scripts/01_data_import_and_clean.R")
   source("scripts/02_eda.R")
   source("scripts/03_modeling.R")
   source("scripts/04_visualization.R")
   ```

5. **Launch the Shiny dashboard:**
   ```r
   shiny::runApp("app.R")
   ```

---

## Interactive Dashboard

The Shiny app provides three interactive views:

- **Explorer** — Scatter plot with selectable X/Y variables, state filtering, and a live Pearson correlation coefficient
- **State Comparison** — Box plots comparing county-level distributions across selected states
- **Regression** — Choose predictors, fit a linear model, and view coefficient tables with residual diagnostics

> *[If you deploy to shinyapps.io, add the link here:]*
>
> **Live app:** [https://your-username.shinyapps.io/county-health-outcomes/](https://your-username.shinyapps.io/county-health-outcomes/)

---

## Methods

- **Data cleaning:** Removed state-level summary rows (FIPS ending in `000`). Dropped counties missing the primary outcome variable. Documented all exclusion decisions in the cleaning script.
- **Exploratory analysis:** Assessed distributions, identified outliers, and examined bivariate relationships using scatter plots and a correlation matrix.
- **Modeling:** Multiple linear regression with premature death rate as the outcome. Model assumptions (linearity, normality of residuals, homoscedasticity) checked via diagnostic plots.
- **Visualization:** Choropleth map using `sf` and `tigris` shapefiles. Multi-panel figures composed with `patchwork`.

---

## Limitations

- This is an ecological (county-level) analysis — associations observed at the county level cannot be attributed to individuals ([ecological fallacy](https://en.wikipedia.org/wiki/Ecological_fallacy)).
- Cross-sectional design; no causal claims can be made.
- Some counties have small populations and less stable estimates.
- Measures from different data years are combined in the CHR dataset.

---

## Session Info

> *[Paste the output of `sessionInfo()` here after completing your analysis.]*

```r
# Run this at the end of your final script:
sessionInfo()
```

---

## License

This project is for educational and portfolio purposes. The County Health Rankings data is publicly available from the [University of Wisconsin Population Health Institute](https://www.countyhealthrankings.org/).

---

## Author

**[Your Name]** — Public health researcher building data analysis skills in R.

- GitHub: [@your-username](https://github.com/your-username)
- LinkedIn: [your-profile](https://linkedin.com/in/your-profile)
