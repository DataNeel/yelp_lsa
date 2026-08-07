# Obvious repo guidance

<!-- obvious-install: skill=autobuild-setup, skill-version=1.0.3, template-version=1 -->

This repo uses `.obvious/` for reviewed Autobuild guidance.

Before editing, suggest the smallest relevant set of `.obvious` files for the task. Match candidate files by reading their frontmatter.

## Codebase Map

| Path | Purpose |
|---|---|
| `yelp_lsa.ipynb` | Jupyter notebook — LSA and K-means clustering on Yelp business/review data |
| `README.md` | Project description with nbviewer link |

## Repo Guidance for Autobuild

No AGENTS.md, CLAUDE.md, CONTRIBUTING.md, or .cursorrules found. No specific agent guidance from repo docs.

**Stack:** Python (notebook authored for Python 2.7), Jupyter. Dependencies: pandas, numpy, matplotlib, scikit-learn, scipy, mpl_toolkits.basemap.

**Data dependency:** The notebook reads `../yelp_academic_dataset_business.json` and `../yelp_academic_dataset_review.json` — external Yelp Academic Dataset files not included in the repo. These must be downloaded separately from Yelp and placed in the parent directory.

**Kernel note:** The notebook metadata specifies a `python2` kernel. The sandbox only has `python3` and `javascript` kernels. Execution with `--ExecutePreprocessor.kernel_name=python3` gets past the kernel issue but fails on the `mpl_toolkits.basemap` import.

## Local Verification

> **Warning:** Running full-repo typecheck, lint, or tests may OOM or timeout in the sandbox for large repos.
> Use the scoped commands below when verifying changes.

### Verified Commands

- **Dependency install:** `pip install pandas numpy matplotlib scikit-learn scipy` — PASS
- **Import check:** `python3 -c "import pandas, numpy, matplotlib, sklearn, scipy; print('OK')"` — PASS
- **Kernel:** `python3 -m jupyter nbconvert --version` — PASS (7.17.1)
- **Notebook execution:** FAIL — `mpl_toolkits.basemap` not installed (ModuleNotFoundError); also requires external data files and python2 kernel

### Scoped Workflow

1. **Verify deps:** `pip install pandas numpy matplotlib scikit-learn scipy && python3 -c "import pandas, numpy, matplotlib, sklearn, scipy"`
2. **Run notebook:** `python3 -m jupyter nbconvert --to notebook --execute yelp_lsa.ipynb --ExecutePreprocessor.kernel_name=python3` (requires `mpl_toolkits.basemap` install + Yelp data files in parent directory)

## Sandbox Snapshot

- **Snapshot ID:** N/A — snapshot not captured (partial dev stack; snapshot tool not available in this execution context)
- **Captured:** N/A
- **Dev stack healthy:** partial — dependencies install and imports verified, but notebook execution fails due to missing `mpl_toolkits.basemap` and external data files

## Bibliography

Product Atlas already contained a comprehensive hierarchy for this repo under product node `bib_XWEYujFr` ("Yelp Latent Semantic Analysis", slug `yelp-lsa`) with 6 concept children and 12 feature children covering business clustering, geographic analysis, LSA, review text vectorization, semantic search, and data preparation.

Autobuild-setup scan upserted 1 additional node:

- **System node** `bib_1knLXlzD` — "Yelp LSA Notebook" (slug `yelp-lsa-notebook`), attached to product `bib_XWEYujFr`, with file provenance from `yelp_lsa.ipynb`.

## Security Scan

> **Note:** security_scan_not_triggered — tool not available in this environment.

## Runbooks

Populated by autobuild-runbooks skill when requested. See `.obvious/runbooks/` after that skill runs.

