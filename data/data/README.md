# Data

**Source:** Figure 2 in Voight et al. (2012), *Plasma HDL cholesterol and risk of myocardial infarction: a mendelian randomisation study*, The Lancet 380: 572–580. https://doi.org/10.1016/S0140-6736(12)60312-2

The numbers were typed in by hand from the figure. The same values are also written directly in the notebook (cell 3), so the notebook runs without this file, for example when opened in Google Colab.

**File:** `cohorts.csv`, 6 rows (one per prospective cohort study) and 6 columns:

| Column | Meaning |
|---|---|
| `study` | Study name: ARIC, CCHS, DCH, FHS, HPFS, MDC |
| `OR` | Odds ratio for myocardial infarction per copy of the HDL-raising LIPG 396Ser allele |
| `lower` | Lower limit of the 95% confidence interval |
| `upper` | Upper limit of the 95% confidence interval |
| `cases` | Number of participants who developed myocardial infarction |
| `controls` | Number of participants without myocardial infarction |

The odds ratios are adjusted for age and sex in the original studies and are rounded to two decimals in the paper. The cases and controls are included for reference and are not used in the analysis.
