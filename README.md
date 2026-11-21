# Predictors of Canadian Youth Vaping

[![Badge linking to python.org](https://img.shields.io/badge/Python-9F225F?logo=python&logoColor=white)](https://www.python.org/)
[![Badge linking to duckdb.org/](https://img.shields.io/badge/Duckdb-9F225F?logo=Duckdb&logoColor=white)](https://duckdb.org/)

Author: Carter M. Smith

Published: 2026-09-18; [`Version 1`](https://github.com/cartermsmith/predictors-youth-vaping/tree/v1.0).

Revised: 2026-11-21

An analysis of psychological predictors that are associated with the likelihood that a young person in Canada (aged 12-17), who has tried vaping, has used an e-cigarette over the past month. Data comes from the [2022 Canadian Community Health Survey Public Use Microdata File (CCHS-PUMF)](https://www150.statcan.gc.ca/n1/en/catalogue/82M0013X).

## Summary

- Counterintuitively, a *weakened* sense of youth community belonging was associated with *reductions* in the likelihood of self-reported e-cigarette use in the last month.

- Higher life satisfaction ratings were marginally related to decreases in past-month use.

- Two machine learning classifiers performed modestly above chance when discriminating between current and past e-cigarette users (AUC ~.57-.60).

- Additional measures beyond the psychological variables examined here appear necessary to assess how Canadian youth use e-cigarettes once they've tried them.

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
- Modelling: Logistic regression (`statsmodels`); random forest (RF) and logistic regression machine learning classifiers (`sklearn`) with 10-fold cross-validation. AUC was used for model performance.
- Diagnostics: Multi-collinearity checked with VIF.

## Limitations

- These data are cross-sectional. No causal conclusions can be made about the observed associations.

- Survey weights were not used; conclusions are limited to the sample here, rather than Canadian youth writ-large.

- For additional limitations and speculative next steps, see the *Limitations & Next Steps* section of `brief.qmd` / `brief.pdf`.

## Acknowledgements

- The PrettyPDF Quarto extension from Nicola Rennie was used when creating the brief. Check it out using the citation below!

*Rennie, Nicola. 2023. “Making Pretty PDFs with Quarto.” February 17. https://nrennie.rbind.io/blog/pdf-quarto/making-pretty-pdf-quarto/.*

- Data source note:

*Source: Statistics Canada, 2022 Canadian Community Health Survey Public Use Microdata File, 2022. Reproduced and distributed on an "as is" basis with the permission of Statistics Canada.*