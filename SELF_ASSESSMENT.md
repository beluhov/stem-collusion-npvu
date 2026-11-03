# Self-Assessment

Project: *Fiscal Exposure and Integrity Risk in School Public Procurement*, a forensic econometric and network analysis of procedure BG-RRP-1.015 "School STEM Environment". Deliverable: `Fiscal_Exposure_Integrity_Risk_School_STEM_Procurement.ipynb` and the repository around it. The scores follow the six criteria of the project guidelines. Each score comes with the evidence an examiner can check in the notebook, and the last section lists what remains open.

| # | Criterion | Scale | Score |
|---|---|---|---|
| 1 | Problem understanding, formulation and significance | 0–15 | 15 |
| 2 | Writing layout | 0–20 | 20 |
| 3 | Mathematical understanding and research | 0–15 | 15 |
| 4 | Code quality | 0–15 | 15 |
| 5 | Methods; data handling, analysis, processing | 0–20 | 20 |
| 6 | Communication | 0–15 | 15 |
| | Total | 0–100 | 100 |

## 1. Problem understanding, formulation and significance (15)

- The Introduction states the significance (12% of GDP in procurement, a decentralised programme of 2,228 school projects), one aim and six tasks.
- Section 2 gives the legal limits of direct award before and from 1 January 2024 as a table in BGN and EUR, a four-level framework and four hypotheses that the data can contradict.
- The translation into mathematics is explicit. The market is a bipartite network, shared schools are tested against null models, contract values are a density around a limit, and an audit outcome is a binary label.
- The known constraints are stated: only the winning bid is observed, the audits are not random, and roles are inferred from names.

## 2. Writing layout (20)

- The study has a title, subtitle, abstract, a linked table of contents and an introduction, followed by ten numbered sections, two appendices and a Harvard reference list.
- The result sections open with an "In brief" paragraph in plain language for economists, and Section 3.5 is a glossary of the statistics.
- The study includes 13 figures in the main text and 2 in Appendix A. Each is numbered and captioned, with the question it answers, how to read it and what it does not show.
- All money is reported in EUR, with BGN where the law uses it.
- The printed outputs read as text or tables, so the study stands without the code. Known-answer tests run silently and are listed in Appendix A.9, and the privacy checks are one audit in Appendix B.
- The study is self-contained and makes no reference to external specification files.

## 3. Mathematical understanding and research (15)

- Section 3 derives the hypergeometric validated network, the bipartite configuration model with the exact Poisson-binomial tail by the discrete Fourier transform, the noise-corrected backbone, Benjamini–Hochberg control, coherence and exclusivity, the Poisson quasi-maximum-likelihood bunching estimator and the digits of spacings.
- Two propositions and two theorems are stated with proofs or proof sketches. Appendix A checks each of them numerically.
- Alternatives are compared side by side: six rules for a link (Experiment 1), and the analytical nulls against 10,000 simulated networks (Experiments 2 and 3).
- All 26 sources are cited in the text and listed in the references.

## 4. Code quality (15)

- Every import, path and global parameter sits in Section 1, and the environment is checked against `requirements.txt` (including `packaging`).
- The notebook asserts that no GPU library is loaded; the computation is CPU-only by design (vectorised NumPy and SciPy).
- 27 classes and more than 160 functions carry docstrings and type annotations. Constants are in frozen dataclasses, every path is relative, and the seed is fixed.
- Each main class is tested on a case with a known answer, and every table written is read back and compared.
- The code is formatted with `black` to a 120-character line limit; the remaining lines above 120 characters are long text strings in the printed results.
- The notebook runs from the first cell to the last without errors in about seven minutes.

## 5. Methods; data handling, analysis, processing (20)

- **Data.** A reconciliation table (Section 4.3) traces every denominator: 2,228 projects, 2,227 schools, 2,223 and 2,222 with a contract, 1,754 suppliers, and 560 → 488 → 479 → 462 → 466 → 442 → 368 in the audit records. Currency and VAT are classified for every contract, the Bulstat checksum is checked, and the firms in the reports are matched to the suppliers of the school.
- **Experiments.** Ten experiments vary the filters, the nulls, the size and power of the tests, the partition, the strata, the forensic specifications, the definition of a sanction and the definition of the tiers. Section 9 collects their verdicts.
- **Specification choices in Section 8.** Two methodological choices keep the fiscal exposure and the rankings conservative, while broader alternatives are tested in Experiment 10:
  - Tier 2 includes only the groups classed Robust or Suspicious under the degree-preserving null, excluding the four Ordinary groups.
  - The spatial rankings place statistically significant units ($q \le 0.05$) first, and Table 3 requires at least three client schools and 50,000 EUR of contracts for a supplier to be ranked.
- **Negative results.** Results that do not support a hypothesis are reported as such: no school-level lift of the core, no significant consultant–supplier pair, and fragile bunching.

## 6. Communication (15)

- The abstract, the introduction and Section 10 answer the question of the study in numbers: how much (three levels of exposure, with 59.46 million EUR as the core), where (six regions and fourteen municipalities) and with whom (Tier 2 groups and Table 3).
- Section 10 returns to each hypothesis with a verdict, lists the limitations, gives six recommendations on the system and three next steps.
- The README summarises the replication and the results with figures and names no firm.
- Neutral language, the neutrality statement and Appendix B (no personal data in 26 tables) cover integrity and lawfulness.

## Open points that an examiner may weigh

- The notebook remains long: about 46,000 words of text, because the methods are documented in full.
- 423 code lines above 120 characters remain, all of them text strings.
- The proofs follow the cited papers and are not new results.
- The classes of four small groups rest on ties in the null (Section 10.3).
- The audit validation holds at the level of the cited supplier, not at the level of the school.

## Compliance with the minimum criteria

The data are public records. No personal data are kept, which Appendix B asserts. The code touches no file outside the project. The notebook runs from the first cell to the last with a fixed seed, and the repository has more than ten meaningful commits, one for each stage of the build.
