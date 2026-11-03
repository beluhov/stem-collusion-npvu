# stem-collusion-npvu

Forensic screening of the procurement of the Bulgarian procedure BG-RRP-1.015 "School STEM Environment" (Recovery and Resilience Plan, NPVU). The project is one Jupyter notebook, `Final_Exam_Procurement_Collusion.ipynb`, written in English, with the mathematics, the algorithms implemented from scratch, ten experiments and the data they use.

The question: do the contracts of the 2,222 schools of the procedure show patterns of the kind that the literature links to restricted competition and manipulated values, and how much of the contracted value do such patterns touch? The answer is given as risk indicators. **A statistical anomaly is not evidence of a violation.** No school, supplier or person is accused of anything, and the notebook contains no personal names and no personal identification numbers.

## What the notebook does

| Part | Sections of the notebook |
|---|---|
| Setting, legal limits, problem and four hypotheses | 2 to 4 |
| Theory (statistically validated network, bipartite configuration model, Benjamini–Hochberg, coherence and exclusivity, bunching, Benford spacings) and numerical checks of two propositions and two theorems | 5, 6 |
| Environment, ingestion of ISUN 2020, normalisation of currency and VAT, ADFI reports, bipartite market | 1, 7, 8, 9 |
| Experiments: backbones, Monte Carlo null, groups, spatial concentration, forensic indicators, validation against the audits, fiscal exposure | 10 to 15 |
| Conclusions, limitations, recommendations, neutrality statement, Harvard references | 16, 17, References |

Main results (details and limits in Section 16):

- The overlap of the two largest suppliers (581 and 298 schools) is explained by their degrees: under the bipartite configuration model 1 of 621 and 0 of 316 links remain. One group of three suppliers stays far above the null.
- Consultant precedence is not a general pattern: no consultant–supplier pair has an adjusted q below 0.01.
- Municipal schools are more aligned with the leading suppliers of their municipality than state schools (gap +0.090, permutation p = 0.001).
- The flags of the three tiers are weakly associated with the sanctions of the audits (lift 1.024, permutation p = 0.002, base rate 83.3%).
- 4,732 contracts carry a flag: 124.19 million EUR including VAT, 43.0% of the contracted value. This is an exposure, not a loss.

## Repository

```
Final_Exam_Procurement_Collusion.ipynb   the notebook, executed
requirements.txt                         minimum versions of the packages
data/                                    working tables created from the sources (no personal data)
data/derived/                            results of the notebook, small CSV files
SELF_ASSESSMENT.md                       self-assessment against the six criteria of the guidelines
LICENSE
```

`data/raw/` (copies of the sources) and `data/cache/` (large arrays) are not in the repository. The sources are the open data of ISUN 2020 (https://2020.eufunds.bg/bg/0/0/OpenData), the public register of ADFI inspection reports (https://www.adfi.minfin.bg/bg/34) and the list of schools of the Ministry of Education and Science. The notebook cites them and opens them only once, in Sections 7 and 8, to create the working tables of `data/`. Every later section reads only `data/` and `data/derived/`.

Files of `data/derived/`: `contracts.csv` (one row per contract, values in EUR), `project_classes.csv`, `normalized_totals.csv`, `consultant_steering.csv`, `validated_edges.csv`, `validated_groups.csv`, `group_metrics.csv`, `mc_simulation_summary.csv`, `mc_bicm_comparison.csv`, `spatial_risk_indices.csv`, `forensic_risk_flags.csv`, `adfi_matches.csv`, `adfi_supplier_matches.csv`, `adfi_validation_results.csv`, and the four national tables `table_01_municipalities.csv`, `table_02_ruo.csv`, `table_03_contractors.csv` and `table_04_fiscal.csv`. Money columns carry the currency and the VAT basis in the name (`_eur_incl_vat`, `_bgn_excl_vat`).

## Setup and replication

Python 3.13 and the packages of `requirements.txt`:

```
python -m pip install -r requirements.txt
```

Run the whole notebook from the repository root:

```
jupyter nbconvert --to notebook --execute --inplace Final_Exam_Procurement_Collusion.ipynb
```

The random seed is fixed (`SEED = 42`), and the shuffles repeat exactly. Without `data/raw/`, Sections 7 and 8 use the working tables that are already in `data/`; without `data/cache/`, the arrays are recomputed. A full run takes about 7 minutes (7.1 minutes in a copy without `data/raw/` and `data/cache/`, which recomputes the cache) and peaks at about 2.6 GiB of memory; the Monte Carlo ensemble of 10,000 networks is the main part of both.

## Disclaimer

The indicators in this project are diagnostic signals computed from public records. They do not establish illegality, collusion or a violation by any school, supplier, municipality or official, and a flagged contract is not a finding of an audit body.
