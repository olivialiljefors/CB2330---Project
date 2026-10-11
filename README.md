# Does genetically raised HDL cholesterol lower the risk of myocardial infarction?

**Klara Gesché & Olivia Liljefors**, CB2330, autumn 2026

## What this is

A simulation project based on Voight et al. (2012), *Plasma HDL cholesterol and risk of myocardial infarction: a mendelian randomisation study*, The Lancet 380: 572–580.

The paper studies a genetic variant (LIPG Asn396Ser) that raises HDL cholesterol. If HDL protects against myocardial infarction (MI), carriers of the variant should have a lower risk. The paper predicts an odds ratio (OR) of about 0.87. Instead, a meta-analysis of six cohort studies found OR 1.10 (95% CI 0.89–1.37).

We model each cohort's log odds ratio as normally distributed around one common true effect θ:

X_j ~ N(θ, SE_j²)

where SE_j is each study's standard error, calculated from its confidence interval in Figure 2. We then:

1. estimate θ from the six cohort studies by minimising the negative log-likelihood (NLL) over a grid of θ values
2. estimate the uncertainty of θ, both from the curvature of the NLL and from a Monte Carlo simulation of 10 000 repeated six-study experiments
3. simulate the experiment 10 000 times assuming HDL is protective (true OR = 0.87), and count how often the pooled OR comes out at 1.10 or higher

## What we found

| | Our model | Paper |
|---|---|---|
| Pooled OR | 1.105 | 1.10 |
| Standard error of log(OR) | 0.109 (NLL curvature)<br>0.110 (Monte Carlo) | 0.110 |

The paper does not report the standard error directly; we calculated it from the paper's 95% confidence interval (0.89–1.37) in the same way as for the individual studies.

- Our maximum-likelihood estimate reproduces the paper's pooled OR.
- Both of our uncertainty estimates agree with the paper's standard error: the curvature of the NLL gives 0.109, and the spread of the 10000 Monte Carlo estimates gives 0.110.
- **If the true OR were 0.87, a pooled OR of 1.10 or higher would appear in only about 1.6% of simulated experiments.** The observed result is therefore unlikely if raising HDL through this variant protects against MI. This supports the paper's conclusion.

The simulation results vary slightly between runs because of random sampling.

**Limitations:** the model assumes one common effect for all six cohorts, treats the standard errors from the rounded confidence intervals as exact, and uses a normal approximation that may be poor for the smallest studies. It only describes the association between the variant and MI. The conclusion about HDL relies on the paper's mendelian randomisation assumptions, for example that the variant affects MI only through HDL.

## How to run it

Open the notebook in Google Colab and run all cells from top to bottom.

The two Monte Carlo simulations take a few minutes to run.

## Contents

| File | What it is |
|---|---|
| `README.md` | Summary of the project and its findings. Instructions on how to run the code |
| `project.ipynb` | The project card and all analysis |
| `data/` | Odds ratios and confidence intervals for the six cohort studies, from Figure 2 of the paper |
| `data/README.md` | Where the data came from and what the columns mean |

 
