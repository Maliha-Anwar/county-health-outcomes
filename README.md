# County-Level Socioeconomic Determinants of Health Outcomes

**Do counties with lower incomes, higher uninsured rates, and less education have higher rates of premature death?**

This project uses the 2025 County Health Rankings dataset to explore how socioeconomic conditions relate to premature mortality across ~3,000 U.S. counties. The analysis covers data wrangling, exploratory visualization, multiple linear regression, and reproducible reporting. Everything was built in R with Quarto.

---

## Key Findings

> *Findings will be added here as the analysis progresses.*

---

## Data

The analysis uses the **2025 County Health Rankings CSV Analytic Data**, published by the University of Wisconsin Population Health Institute and the Robert Wood Johnson Foundation. The dataset is freely available at [countyhealthrankings.org](https://www.countyhealthrankings.org/health-data/methodology-and-sources/data-documentation).

From the 796 available variables, I selected eight measures spanning health outcomes and socioeconomic factors:

| Variable | Description |
|----------|-------------|
| Premature death | Years of Potential Life Lost per 100,000 |
| Diabetes prevalence | % of adults with diabetes |
| Uninsured | % without health insurance |
| Median household income | County median income ($) |
| Some college | % with some postsecondary education |
| Unemployment | Unemployment rate (%) |
| Adult smoking | % of adults who smoke |
| Adult obesity | % of adults with obesity |

---

## Analysis Pipeline

All analysis lives in a single Quarto document (`analysis.qmd`) and follows a standard epidemiologic workflow:

1. **Data import & cleaning** — Loaded the raw CSV (796 columns, coded variable names), selected and renamed key variables, assessed missingness patterns, filtered state-level summary rows, and converted proportions to percentages.

2. **Exploratory data analysis** — Examined distributions, identified outliers, and assessed bivariate relationships through scatter plots and a correlation matrix to inform variable selection for modeling.

3. **Regression modeling** — Fit a multiple linear regression predicting premature death rate from socioeconomic predictors. Checked model assumptions using residual and Q-Q diagnostic plots.

4. **Interpretation & limitations** — Discussed effect sizes, statistical significance, and key limitations including the ecological fallacy (county-level associations cannot be attributed to individuals).

---

## Skills Demonstrated

- Data wrangling with real-world, messy public health data (tidyverse, janitor)
- Exploratory visualization and correlation analysis (ggplot2, corrplot)
- Multiple linear regression with diagnostic assessment (broom, gtsummary)
- Reproducible reporting with Quarto
- Version control with Git and GitHub

---

## How to Reproduce

1. Clone this repository
2. Download the 2025 CHR CSV Analytic Data from [countyhealthrankings.org](https://www.countyhealthrankings.org/health-data/methodology-and-sources/data-documentation) and save it in `data-raw/`
3. Open `Socioeconomic Factors.Rproj` in RStudio
4. Render `analysis.qmd`

The raw data is not included in this repo due to file size. The cleaned dataset is generated automatically during rendering.

**Packages:** tidyverse · janitor · skimr · corrplot · broom · gtsummary

---

## About This Project

About This Project
I originally worked on this analysis a while back to apply my data analysis skills to a public health research question. I recently decided to clean it up and put it on GitHub as a portfolio piece. My background is in applied public health research, and I'm actively expanding my quantitative toolkit in R.

## Author

**Maliha Anwar** · Public Health Researcher
