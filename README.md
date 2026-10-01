
<h1 align="center">STAT 380 – Mini Project 1</h1>

<p align="center"><b>Contributing Members:</b><br>Ian Peralta, Ashley Song, Bryan Xiao</p>

**Course:** STAT 380
**Data source:** [Gapminder](https://www.gapminder.org/data/)

## Overview

In this project we use country-level data from Gapminder to explore and model total population. Our response variable is population, and we use six predictors: children per woman, CO2 emissions per capita, happiness score, income groups, people in poverty and basic sanitation access. We combine the datasets into a single country-level data set, perform exploratory data analysis, fit and compare linear models, and answer a question of our own using a data visualization.

## Research Question

> Is the number of people living in poverty associated with access to basic sanitation across countries in 2022?

Yes, moderately. Across 174 countries the correlation is -0.403, so countries with more people in poverty tend to have lower access to basic sanitation. This is an association and does not show that one causes the other.

## Repository Structure

```
STAT380_MiniProject1/
├── data/
│   ├── response/      # Response variable dataset
│   └── predictors/    # Predictor variable datasets
├── scripts/           # Quarto (.qmd) source files
├── renders/           # Rendered output (PDF/HTML) of the .qmd files
├── STAT380_MiniProject1.Rproj
└── README.md
```

## Data

All data come from Gapminder. Each dataset has one row per country (`geo`, `name`) and one column per year. Year columns after 2022 are dropped, so the data cover up to 2022 where available, and the models and final question use the 2022 values.

| Role      | Variable                       | File                                                                     | Type                               | Description                                                                            |
| --------- | ------------------------------ | ------------------------------------------------------------------------ | ---------------------------------- | -------------------------------------------------------------------------------------- |
| Response  | Population                     | `data/response/pop.csv`                                                | Quantitative (discrete, count)     | Total number of people living in each country each year.                               |
| Predictor | Basic sanitation access (%)    | `data/predictors/at_least_basic_sanitation_overall_access_percent.csv` | Quantitative (continuous, percent) | Percentage of people using at least basic sanitation facilities, unshared with others. |
| Predictor | Children per woman (fertility) | `data/predictors/children_per_woman_total_fertility.csv`               | Quantitative (continuous)          | Average number of children a woman would have in her lifetime.                         |
| Predictor | CO2 per capita (consumption)   | `data/predictors/co2_pcap_cons.csv`                                    | Quantitative (continuous)          | Consumption-based CO2 emissions per person, measured in tonnes of CO2.                 |
| Predictor | Happiness score (WHR)          | `data/predictors/hapiscore_whr.csv`                                    | Quantitative (continuous, score)   | National average life evaluation on a 0 to 100 scale.                                  |
| Predictor | Income levels (World Bank)     | `data/predictors/ilevels4_wb.csv`                                      | Categorical (ordinal, 4 levels)    | World Bank income group of each country based on GNI per capita.                       |
| Predictor | People in poverty (number)     | `data/predictors/number_of_people_in_poverty.csv`                      | Quantitative (discrete, count)     | Number of people living on less than $3 a day.                                         |

## Analysis Workflow

1. **Load & combine data** – join the response and predictors into one data set (country name, geo, and yearly values).
2. **Exploratory data analysis** – for each variable: type, possible values, missing data, cleaning, summary statistics, and plots alone and against the response, with a short written interpretation. Extreme outliers are looked up by country, and correlations with log population in 2022 guide the choice of model predictors.
3. **Linear models** – one simple linear regression and two multiple regressions on the 2022 data, with interpreted slopes and residual diagnostics.
4. **Model comparison** – the models are compared using R squared.
5. **Our own question** – a question, a supporting visualization, and an answer.

### Model Results

| Model                         | Predictors                                  | Countries | R squared |
| ----------------------------- | ------------------------------------------- | --------- | --------- |
| Simple linear regression      | People in poverty                           | 186       | 0.225     |
| Multiple linear regression 1  | People in poverty and children per woman    | 186       | 0.306     |
| Multiple linear regression 2  | People in poverty and basic sanitation access | 174     | 0.280     |

The model with people in poverty and children per woman has the highest R squared and is the best of the three. Residual plots for all three models show curved patterns, heavy-tailed residuals and spread that grows with the fitted value, so none of them fits well.

## Files

| File                            | Description                                                 |
| ------------------------------- | ----------------------------------------------------------- |
| `scripts/MiniProject1_Code.qmd` | Main project analysis: data, EDA, models and final question |
| `renders/MiniProject1_Code.pdf` | Rendered PDF of the main analysis                           |
| `renders/data-import-join.pdf`  | Early render of the data import and join steps              |

## How to Reproduce

1. Clone the repository and open `STAT380_MiniProject1.Rproj` in RStudio.
2. Install the required package: `install.packages("tidyverse")`.
3. Render the qmd files from the `scripts/` folder with Quarto, since the data paths are relative, for example `../data/predictors/`.

## Submission Checklist

Each person uploads (members of a group upload the same documents):

- [ ] Data
- [ ] `.qmd` file
- [ ] Rendered HTML or PDF
- [ ] Source disclosure document

**Disclosure document:** for each (named) code chunk, record where the code came from:

- **AI:** the prompt and the response
- **Web search:** the search and the page the code is from
- **Copy-paste-change:** the class document it came from, plus the original code we started from
