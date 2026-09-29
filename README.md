<h1 align="center">STAT 380 – Mini Project 1</h1>

<p align="center"><b>Contributing Members:</b><br>Ian Peralta, Ashley Song, Bryan Xiao</p>

**Course:** STAT 380
**Data source:** [Gapminder](https://www.gapminder.org/data/)

## Overview

<!-- 2–3 sentences: what is this project about? What is the response variable and why did we pick it? -->

In this project we use country-level data from Gapminder to explore and model our response variable using values of several predictor variables. We combine the datasets into a single country-level data set, perform exploratory data analysis, fit and compare linear models, and answer a question of our own using a data visualization.

## Research Question

<!-- The question we answer with our own visualization. Fill in once decided. -->

> *TBD*

## Repository Structure (under construction)

```
STAT380_MiniProject1/
├── data/
│   ├── response/      # Response variable dataset
│   └── predictors/    # Predictor variable datasets
├── scripts/           # Quarto (.qmd) source files
├── renders/           # Rendered output (PDF/HTML) of the .qmd files
└── README.md
```

## Data

All data come from Gapminder. Each dataset has one row per country (`geo`, `name`) and one column per year.

| Role      | Variable                   | File                                                       | Type | Description |
|-----------|----------------------------|------------------------------------------------------------|------|-------------|
| Response  | Population                 | `data/response/pop.csv`                                    | Quantitative (discrete, count) | Total number of people living in each country each year. |
| Predictor | Basic sanitation access (%) | `data/predictors/at_least_basic_sanitation_overall_access_percent.csv` | Quantitative (continuous, percent) | Percentage of people using at least basic sanitation facilities, unshared with others. |
| Predictor | Children per woman (fertility) | `data/predictors/children_per_woman_total_fertility.csv` | Quantitative (continuous) | Average number of children a woman would have in her lifetime. |
| Predictor | CO2 per capita (consumption) | `data/predictors/co2_pcap_cons.csv`                     | Quantitative (continuous) | Consumption-based CO2 emissions per person, measured in tonnes of CO2. |
| Predictor | Happiness score (WHR)      | `data/predictors/hapiscore_whr.csv`                        | Quantitative (continuous, score) | National average life evaluation on a 0 to 100 scale. |
| Predictor | Income levels (World Bank) | `data/predictors/ilevels4_wb.csv`                          | Categorical (ordinal, 4 levels) | World Bank income group of each country based on GNI per capita. |
| Predictor | People in poverty (number) | `data/predictors/number_of_people_in_poverty.csv`          | Quantitative (discrete, count) | Number of people living on less than $3 a day. |

## Analysis Workflow

1. **Load & combine data** – join the response and predictors into one data set (country name, geo, and yearly values).
2. **Exploratory data analysis** – for each variable: type, possible values, missing data, cleaning, summary statistics, and plots (alone and against the response), with a short written interpretation. Investigate extreme outliers by country.
3. **Linear models** – one simple linear regression and two multiple regressions, evaluated with the criteria from class, with interpreted slopes.
4. **Model comparison** – decide which model is best.
5. **Our own question** – a question, a supporting visualization, and an answer.

## Files

| File | Description |
|------|-------------|
| `scripts/Stat380_MiniProject1_Code.qmd` | Main project analysis |
| `scripts/data-import-join.qmd` | Class example for importing and joining data (reference) |
| `renders/data-import-join.pdf` | Rendered class example |
| `renders/` | Renders of the project `.qmd` will go here |


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
