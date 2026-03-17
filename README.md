# Publication effects in anomaly returns (wiPCA / rwiPCA)

This repository reproduces a panel event-study of anomaly portfolio returns around the publication date of the underlying trading strategy.
The empirical object is a large, unbalanced panel of long–short portfolio returns. Publication induces a structured missingness pattern for counterfactual outcomes (post-publication control outcomes are not observed), so the analysis uses a factor-model imputation approach (ridge weighted PCA with fixed effects) to construct counterfactual returns and estimate post-publication effects.

The deliverable is an **illustrative notebook** that executes end-to-end and exports a compact set of figures and tables.

## What is in the data

- `data/raw/portfolio.parquet.gz` is a long-format panel of portfolio returns.
  - The notebook filters to the **long–short (LS)** portfolios.
  - The raw LS panel in this package runs from **1926-01-30 through 2024-12-31**.
- `data/raw/signal_doc.csv` contains signal documentation, including the publication year for each strategy.

The notebook’s analysis sample is **1963-07-31 through 2024-12-31**.

## Quick start

### 1. Create an environment

Using `pip`:

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

### 2. Run the notebook

Open:

- `notebooks/publication_effect_illustrative.ipynb`

and run all cells.

The notebook writes figures and tables to:

- `outputs/notebook_outputs/`

## Outputs

The exported outputs include:

- **Data coverage diagnostics** showing that the panel runs through **2024-12-31** (full-sample coverage, a zoom-in on 2019–2024, and the distribution of each strategy’s last observed month).
- **Figure 2 (main)**: event-time cumulative wealth after publication, excluding the DR-rwiPCA and momentum-controlled rwiPCA variants.
- **Figure 2 (appendix)**: the DR-rwiPCA and momentum-controlled rwiPCA variants shown separately for comparison.
- A complete **strategy-by-sign partition** of estimated publication effects.
- An Appendix-style **inference comparison** (sectioning, Newey–West, moving-block bootstrap, and a conservative analytic benchmark) with a companion bar chart.

## Organization

- `notebooks/` contains the executed illustrative notebook.
- `data/raw/` contains the two input files used by the notebook.
- `outputs/notebook_outputs/` contains exported figures and CSV tables.
- `reports/` contains an HTML export of the executed notebook.

## Notes on methods

The counterfactual construction follows a large-dimensional approximate factor model with missing observations, combined with time and strategy fixed effects. The ridge step stabilizes factor recovery in the presence of unbalanced panels and weak overlap.

For inference on calendar-time aggregated effects, the repository emphasizes resampling-based uncertainty quantification (moving-block bootstrap as the default), and treats closed-form variance expressions as conservative benchmarks.

## References

- Bai, J. (2003). Inferential theory for factor models of large dimensions.
- Lettau, M., and Pelger, M. (2018). Estimating latent asset-pricing factors.
- Pelger, M., and Xiong, R. Large-dimensional factor modeling with missing observations and applications to causal inference.
