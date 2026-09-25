# Predictors of Canadian Youth Vaping

[![Badge linking to python.org](https://img.shields.io/badge/Python-9F225F?logo=python&logoColor=white)](https://www.python.org/)
[![Badge linking to duckdb.org/](https://img.shields.io/badge/Duckdb-9F225F?logo=Duckdb&logoColor=white)](https://duckdb.org/)

Author: Carter M. Smith

Published: 2026-09-18

An analysis of psychological predictors that influence the likelihood that a young person (aged 12-17) in Canada has used an e-cigarette over the past month. Data comes from the [2022 Canadian Community Health Survey Public Use Microdata File (CCHS-PUMF)](https://www150.statcan.gc.ca/n1/en/catalogue/82M0013X).

## Summary

- For every one-unit increase in a young respondent's sense of belonging in the community, the likelihood that they have recently vaped decreases by 10.3 percentage points.

- As youth life satisfaction increases by a single unit, the predicted probability that they have recently vaped is reduced by 3.1 percentage points.

- Policy focused on reducing youth vaping may consider enhancing youth community engagement and targeting overall life satisfaction. Other factors not included here should also be explored. 

## Read the brief

- The [full brief](brief.pdf) includes a concise summary of the methods, results, and limitations of this project.

## Repository contents

| File                           | Description             |
|--------------------------------|-------------------------|
| brief.qmd / brief.pdf          | Concise project brief   |
| cchs-pumf-analysis.qmd / .html | Full technical analysis |
| references.bib                 | Citations               |
| requirements.txt               | Python dependencies     |

## Reproducing the analysis

1. Clone this repository

2. Create a virtual environment, install dependencies:

```
pip install -r requirements.txt
```

3. Download the [CCHS-PUMF CSV](https://www150.statcan.gc.ca/n1/en/catalogue/82M0013X) and place `pumf_cchs.csv` in data/

*Note: Raw data is not redistributed in this project.*

4. Render with Quarto:

```
quarto render cchs-pumf-analysis.qmd
quarto render brief.qmd
```

5. View rendered output in `cchs-pumf-analysis.html` and `brief.pdf`

## Methodology

- Data wrangling: SQL, via DuckDB. Queried/filtered the youth sample. Further cleaning done with `pandas`.
- Modelling: Logistic regression (`statsmodels`); random forest (RF) machine learning classifier (`sklearn`) as a robustness check.
- Diagnostics: Multi-collinearity checked with VIF, AUC-ROC for RF performance.

## Limitations

- For a description of what an attempted robustness check via a machine learning algorithm revealed about the data, see the *Limitations* section of `brief.qmd` / `brief.pdf`.

*Source: Statistics Canada, 2022 Canadian Community Health Survey Public Use Microdata File, 2026-09-18. Reproduced and distributed on an "as is" basis with the permission of Statistics Canada.*