# Publication effects in anomaly returns (wiPCA / rwiPCA)

Reproduces a panel event-study of anomaly portfolio returns around the publication date of the underlying trading strategy.
The empirical object is a large, unbalanced panel of long–short portfolio returns. Publication induces a structured missingness pattern for counterfactual outcomes (post-publication control outcomes are not observed), so the analysis uses a factor-model imputation approach (ridge weighted PCA with fixed effects) to construct counterfactual returns and estimate post-publication effects.

## Data
- `data/raw/portfolio.parquet.gz` is a long-format panel of portfolio returns.
  - The raw LS panel in this package runs from **1926-01-30 through 2024-12-31**.
- `data/raw/signal_doc.csv` contains signal documentation, including the publication year for each strategy.


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

- `notebooks/publication_effect_notebook.ipynb`

and run all cells.

## References

- Bai, J. (2003). Inferential theory for factor models of large dimensions.
- Lettau, M., and Pelger, M. (2018). Estimating latent asset-pricing factors.
- Pelger, M., and Xiong, R. Large-dimensional factor modeling with missing observations and applications to causal inference.
