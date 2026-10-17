# Week 7 — Proteomics

**Date:** 22 October 2026
**Instructors:** Kostas & Erwin
**Theme:** Protein-level regulation, proteoforms, and measurement complexity.

Two exercise notebooks for the session and one to do at home. All run in Colab.

---

## Exercises

### 1 · De novo peptide sequencing

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/UadKLab/27200_Data-Driven-Bioengineering/blob/main/weeks/week07_proteomics/notebooks/01_de_novo_sequencing.ipynb)

**[notebooks/01_de_novo_sequencing.ipynb](notebooks/01_de_novo_sequencing.ipynb)** — read a peptide
sequence from a fragment spectrum by hand, then with a dynamic-programming algorithm, then with the
deep learning model InstaNovo on 100 real HeLa spectra.

> **Select a GPU runtime first** (*Runtime → Change runtime type → T4 GPU*) and run the install cell.
> It takes about 5 minutes and restarts the runtime once.

### 2 · Database search

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/UadKLab/27200_Data-Driven-Bioengineering/blob/main/weeks/week07_proteomics/notebooks/02_database_search.ipynb)

**[notebooks/02_database_search.ipynb](notebooks/02_database_search.ipynb)** — build a protein
database from the human genome with Biopython, digest it with pyOpenMS, add decoys, score 2,000 HeLa
spectra with the hyperscore, and control the false discovery rate with target–decoy competition.
No GPU needed.

## At home

### 3 · From a protein table to a result

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/UadKLab/27200_Data-Driven-Bioengineering/blob/main/weeks/week07_proteomics/notebooks/03_downstream_analysis.ipynb)

**[notebooks/03_downstream_analysis.ipynb](notebooks/03_downstream_analysis.ipynb)** — filtering,
log transformation, missing values, normalization, imputation and statistics on a benchmark dataset
where the right answer is known. Not part of the session.

---

## Data

| File | Contents |
|---|---|
| `data/mystery_spectrum.csv` | a simulated fragment spectrum for Exercise 1, part A |
| `data/mystery_real_spectrum.csv` | the real spectrum of the same peptide (a local copy; the notebook fetches it from PRIDE) |
| `data/hela_100.mgf` | 100 MS/MS spectra from one HeLa run: 80 identified by a database search, 20 not |
| `data/hela_100_reference.csv` | the database-search result for those spectra (MSGF+ with Percolator, 1% FDR) |
| `data/hela_100_instanovo_preds.csv` | InstaNovo predictions for the same spectra, used if the notebook cannot run the model |
| `data/hela_2000.mgf` | 2,000 MS/MS spectra from the same run, for the database search (150 strongest peaks each) |
| `data/hela_2000_reference.csv` | the MSGF+ result for those spectra |
| `data/maxlfq_hela_ecoli_proteinGroups.csv` | protein intensities from the MaxLFQ benchmark (HeLa with E. coli at 1× and 3×) |

Spectra come from `11052020_HeLa09.raw` in
[PXD045495](https://www.ebi.ac.uk/pride/archive/projects/PXD045495) (Pierce HeLa digest, Orbitrap
Eclipse, HCD, Orbitrap MS2). Each spectrum's title is its universal spectrum identifier (USI), so any
spectrum can be viewed in the PRIDE archive. The quantification benchmark is
[PXD000279](https://www.ebi.ac.uk/pride/archive/projects/PXD000279) (Cox et al., *Mol Cell Proteomics*
2014).

## Acknowledgements

The InstaNovo steps in Exercise 1 are adapted from the de novo practical of the
[Paleoproteomics Summer School 2026](https://github.com/UadKLab/paleoproteomics_summer_school)
(Yun Chiang, Jemma Daniel, Jeroen van Goey). Sample-preparation slides adapted from Erwin M. Schoof.
