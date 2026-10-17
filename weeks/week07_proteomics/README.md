# Week 7 — Proteomics

**Date:** 22 October 2026
**Instructor:** Kostas
**Theme:** Protein-level regulation, proteoforms, and measurement complexity.

Two exercises in class and one optional exercise. All run in Colab.

---

## Exercises

### 1 · Database search

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/UadKLab/27200_Data-Driven-Bioengineering/blob/main/weeks/week07_proteomics/notebooks/01_database_search.ipynb)

**[notebooks/01_database_search.ipynb](notebooks/01_database_search.ipynb)** — build a protein
database from the human genome with Biopython, digest it with pyOpenMS, add decoys, score 2,000 HeLa
spectra with the hyperscore, and control the false discovery rate with target–decoy competition.
No GPU needed; it runs in about two minutes.

### 2 · From a protein table to biology

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/UadKLab/27200_Data-Driven-Bioengineering/blob/main/weeks/week07_proteomics/notebooks/02_downstream_analysis.ipynb)

**[notebooks/02_downstream_analysis.ipynb](notebooks/02_downstream_analysis.ipynb)** — Part A goes
through filtering, log transformation, missing values, normalization, imputation and testing on a
benchmark where the right answer is known. Part B analyses a real experiment (loss of the tumour
suppressor FLCN in kidney cells): t-test, multiple testing correction, volcano plot, enrichment
analysis with g:Profiler, and pathway analysis with Reactome.

### 3 · De novo peptide sequencing (optional)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/UadKLab/27200_Data-Driven-Bioengineering/blob/main/weeks/week07_proteomics/notebooks/03_de_novo_sequencing.ipynb)

**[notebooks/03_de_novo_sequencing.ipynb](notebooks/03_de_novo_sequencing.ipynb)** — do this in
class if there is time, or at home. Read a peptide sequence from a fragment spectrum by hand, then
with a dynamic-programming algorithm, then with the deep learning model InstaNovo on 100 real HeLa
spectra.

> **Select a GPU runtime first** (*Runtime → Change runtime type → T4 GPU*) and run the install cell.
> It takes about 5 minutes and restarts the runtime once.

---

## Data

| File | Used in | Contents |
|---|---|---|
| `data/hela_2000.mgf` | 1 | 2,000 MS/MS spectra from one HeLa run (150 strongest peaks each) |
| `data/hela_2000_reference.csv` | 1 | the database-search result for those spectra (MSGF+ with Percolator, 1% FDR) |
| `data/maxlfq_hela_ecoli_proteinGroups.csv` | 2A | protein intensities from the MaxLFQ benchmark (HeLa with E. coli at 1× and 3×) |
| `data/flcn_ko_proteinGroups.csv` | 2B | protein intensities from FLCN-knockout and control kidney cells |
| `data/mystery_spectrum.csv` | 3 | a simulated fragment spectrum to sequence by hand |
| `data/mystery_real_spectrum.csv` | 3 | the real spectrum of the same peptide (a local copy; the notebook fetches it from PRIDE) |
| `data/hela_100.mgf` | 3 | 100 MS/MS spectra from the same HeLa run: 80 identified by a database search, 20 not |
| `data/hela_100_reference.csv` | 3 | the database-search result for those spectra |
| `data/hela_100_instanovo_preds.csv` | 3 | InstaNovo predictions for the same spectra, used if the notebook cannot run the model |

Spectra come from `11052020_HeLa09.raw` in
[PXD045495](https://www.ebi.ac.uk/pride/archive/projects/PXD045495) (Pierce HeLa digest, Orbitrap
Eclipse, HCD, Orbitrap MS2). Each spectrum's title is its universal spectrum identifier (USI), so any
spectrum can be viewed in the PRIDE archive. The benchmark in Exercise 2A is
[PXD000279](https://www.ebi.ac.uk/pride/archive/projects/PXD000279) (Cox et al., *Mol Cell Proteomics*
2014). The FLCN experiment in Exercise 2B is
[PXD021346](https://www.ebi.ac.uk/pride/archive/projects/PXD021346) (Glykofridis et al., *eLife* 2021).

## Acknowledgements

The InstaNovo steps in Exercise 3 are adapted from the de novo practical of the
[Paleoproteomics Summer School 2026](https://github.com/UadKLab/paleoproteomics_summer_school)
(Yun Chiang, Jemma Daniel, Jeroen van Goey).
