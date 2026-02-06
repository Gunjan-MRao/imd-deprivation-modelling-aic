IMD 2025 Deprivation Modelling (AIC + Diagnostics) & Domain PCA (National vs London)
Analyse the Index of Multiple Deprivation (IMD) 2025 domain patterns across UK Local Authority Districts (LADs) using (1) linear modelling with AIC-based selection + diagnostics and (2) PCA on the seven IMD domains, including a National vs London comparison.

What this project covers
This repo contains two focused analyses (written in R Markdown):

Linear models + AIC + diagnostics: fit and compare linear models for IMD “Overall” using the seven domain scores, with model selection and diagnostic checks.
​

PCA on domains: run PCA on the seven domain variables nationally, then repeat for London-only, and compare variance explained and PC1 loadings side-by-side.
​

Data
The notebooks expect CSVs in data/ (one level above notebooks/):

data/imd2025_individual.csv (used in the linear modelling notebook)
​

data/imd2025_group.csv (used in the PCA notebook)
​

Expected columns (validated early in the notebooks):

Identifiers: LAD24CD, LAD24NM

Targets/metadata: Overall, Rank, Region

Domain variables (7): Income, Employment, Education, Health, Crime, Barriers, Living

If any required columns are missing, the notebooks stop with a clear error message.

Methods (high level)
1) Linear modelling (AIC + diagnostics)
Loads LAD-level IMD data and selects the seven domains plus overall score.
​

Uses linear modelling and AIC-driven selection (via olsrr) to identify a parsimonious specification.
​

Produces model diagnostics to check assumptions and potential issues (e.g., residual patterns, influential points).
​

2) PCA on seven domains (National + London)
Runs PCA (prcomp) on the seven domains with centring and scaling.
​

Produces scree plots and variable biplots to interpret variance explained and domain loadings.
​

Filters to London (Region == "London") to compare PCA structure with the national picture.
​

Builds comparison tables for variance explained (PC1–PC3) and PC1 loadings, and notes that PCA component signs can flip (so sign differences may reflect a sign flip rather than a “real” reversal).
​

Outputs
The PCA Rmd is configured to render an HTML report to:

outputs/02_pca_domains.html
​

The notebooks also generate tables and plots inline (scree plots, biplots, loadings comparisons).
​

Tech stack
R packages used (as shown in notebooks):

Core wrangling/visualisation: tidyverse, ggrepel
​

Modelling helpers: broom, olsrr
​

PCA visualisation: factoextra
​

How to run
Option A: RStudio (recommended)
Clone the repo.

Put the CSVs in data/ (see filenames above).

Open the .Rmd files and click Knit to HTML.

Option B: Command line
From the project root, you can render using rmarkdown::render() (paths depend on your repo structure).

Notes / limitations
This is an analytical project intended to explore relationships and structure in IMD domain data; it is not a deployed model.

Interpretation should be cautious: domain variables may be correlated, and PCA/linear models summarise patterns rather than establish causality.

Coursework note
This work was completed as part of Coventry University coursework and is shared here as a learning + portfolio project.
