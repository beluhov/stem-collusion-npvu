# Self-Assessment

Project: forensic screening of the procurement of the procedure BG-RRP-1.015 "School STEM Environment". Deliverable: `Final_Exam_Procurement_Collusion.ipynb` and the repository around it. The points follow the six criteria of the project guidelines. The scores are my own estimate; the evidence is given so that they can be checked.

| # | Criterion | Scale | My score |
|---|---|---|---|
| 1 | Problem understanding, formulation and significance | 0–15 | 13 |
| 2 | Writing layout | 0–20 | 16 |
| 3 | Mathematical understanding and research | 0–15 | 13 |
| 4 | Code quality | 0–15 | 12 |
| 5 | Methods; data handling, analysis, processing | 0–20 | 16 |
| 6 | Communication | 0–15 | 12 |
| | Total | 0–100 | 82 |

## 1. Problem understanding, formulation and significance

**Evidence.** Sections 2 to 4 set the legal limits of direct award (Public Procurement Act, Art. 20(4), before and from 1 January 2024), the four-level framework and four hypotheses that the data can contradict. The significance is stated: a programme in which about 2,200 schools bought similar equipment, financed from the Recovery and Resilience Plan. The translation to mathematics is explicit: a bipartite network of schools and suppliers, a null model for the shared schools, a density of contract values around a limit, and an audit outcome as a binary label.

**Limits.** The hypotheses about the influence of directorates and municipalities (levels 2 and 3) stay hypotheses, because the data have no record of contacts. Only the winner of a procurement is observed, so competition is inferred and not measured (Section 16.3).

## 2. Writing layout

**Evidence.** 17 numbered sections with subsections, an abstract and a reader's guide, 48 figures with captions, the question, the reading rule and the limit stated for each figure, a summary of the checks at the end of each section, and one Harvard reference list. The language is neutral: the notebook speaks of risk indicators and contracts signed before the project start.

**Limits.** The notebook is long (438 cells, 23 MB with the figures), and a reader needs the guide to find the way. Some captions are not numbered in the same way (Table 1 to Table 4 are numbered, other tables are not).

## 3. Mathematical understanding and research

**Evidence.** Section 5 gives the theory in LaTeX: the hypergeometric validated network, the bipartite configuration model with the exact Poisson-binomial distribution by the Fourier transform, the noise-corrected backbone, Benjamini–Hochberg, coherence and exclusivity, the Poisson quasi-maximum-likelihood estimator of bunching, and the distribution of the digits of spacings. Two propositions and two theorems are stated with proofs or proof sketches, and Section 6 checks each of them numerically on a known case. The alternatives are laid out for comparison (SVN against BiCM against disparity and noise-corrected filters, Experiment 1).

**Limits.** The proofs follow the cited papers and are not new results. Theorem 1 assumes independent p-values for the true nulls, and the tests of the pairs of suppliers are not independent. The notebook says so, treats the bound as an assumption for the network tests, and checks the size of the tests on simulated networks in Experiment 3.

## 4. Code quality

**Evidence.** 27 classes and 162 functions, all classes and 142 of 162 functions with a docstring (the others are `__init__` methods and three small helpers) and type annotations on all but one function, constants collected in frozen dataclasses, relative paths only, a fixed seed, and a test on a case with a known answer for each of the main classes. Every working table is read back and compared with the table that was written. A copy of the project without `data/raw/` and `data/cache/` executes to the end and gives the same files (the same SHA-256 hashes).

**Limits.** Many lines are longer than the 79 characters of PEP 8 (a limit of 120 is exceeded in about 1,450 lines). The `__init__` methods have no separate docstring, because the docstring of the class describes them. All code is in the notebook and not in a package, which makes reuse harder. A full run takes about 7 minutes and peaks at about 2.6 GiB of memory, which is more than a light notebook needs.

## 5. Methods; data handling, analysis, processing

**Evidence.** Ten experiments vary the assumptions: the filters (Experiment 1), the Monte Carlo null against the analytical nulls, the size of the tests and the power against a planted group (Experiments 2 to 5), the partition (6), the gap between municipal and state schools (7), the four forensic indicators (8), the definition of the sanction (9) and of the tiers (10). The data pipeline has documented invariants (11,128 contracts, 1,755 suppliers, 560 reports), a classification of currency and VAT for every contract, a check of the Bulstat checksum, and a matching of the firms in the reports to the suppliers of the school in ISUN. The null models are permutations within strata, with fixed seeds. Results that do not support a hypothesis are reported as such (no consultant–supplier pair has q < 0.01; Tier 2 has lift below 1).

**Limits.** The effects against the audits are small (lift 1.024 against a base rate of 83.3%), the audits are not a random sample, the texts of the reports are read by machine, the roles of the suppliers are inferred from names, and with 1,000 permutations the smallest p-value is 0.001. The results depend on the choices that Experiments 8 to 10 vary, and some are not stable (the fiscal exposure runs from 8.9% to 44.3% of the scheme over seven definitions of the tiers).

## 6. Communication

**Evidence.** The conclusions (Section 16) return to each hypothesis with the numbers and a reading (supported, partly supported), state the limitations, give six recommendations that concern the system and not named parties, and list next steps. The abstract, the README and the neutrality statement say in plain words that an indicator is not a finding of a violation. No personal names or identification numbers are in the code, the outputs or the tables, and the check of the tables for this is an assertion in the notebook.

**Limits.** The notebook is a technical report and not a short article; a reader who wants only the result has to go to Section 16. The recommendations are not tested against alternatives, and the fiscal figures are scenarios by analogy with the rules for structural funds.

## Compliance with the minimum criteria

The data are public records, no personal data are kept, the code does not touch files outside the project, the notebook runs from the first cell to the last with the seed fixed, and the repository has more than ten commits, one for each stage of the build.
