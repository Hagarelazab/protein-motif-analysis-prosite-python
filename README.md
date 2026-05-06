# 🧬 Comparative Protein Motif Analysis  
### Using Python & ExPASy ScanProsite

![Bioinformatics](https://img.shields.io/badge/Bioinformatics-Protein%20Motifs-5DCAA5)
![Python](https://img.shields.io/badge/Python-Regex%20Analysis-3776AB)
![PROSITE](https://img.shields.io/badge/ExPASy-ScanProsite-7B61FF)

---

## 📌 Project Overview

This project focuses on **protein motif detection** in two selected protein sequences from the **APP gene**  
(**Amyloid Beta Precursor Protein**) located on **chromosome 21**.

The aim was to compare:

1. **Python-based motif detection** using regular expressions derived from official PROSITE patterns.
2. **ExPASy ScanProsite**, a web-based bioinformatics motif scanning tool.

The comparison shows the difference between **raw motif counting** using Python and **filtered biological interpretation** using ScanProsite.

---

## 🧬 Gene Studied: APP Gene

The project focuses on the **APP gene**, which stands for:

> **Amyloid Beta Precursor Protein**

APP encodes a transmembrane precursor protein that can be cleaved by secretase enzymes to produce several peptides, including **amyloid-beta**. Amyloid-beta is strongly associated with amyloid plaque formation in **Alzheimer’s disease**.

---

## 🧪 Selected Protein Sequences

The original protein FASTA file contained **11 protein sequences**.  
Two representative protein sequences were selected for motif analysis:

| Protein Accession | Length |
|---|---:|
| `NP_000475.1` | 770 amino acids |
| `NP_001129488.1` | 746 amino acids |

These two sequences were saved in:

```text
selected_two_proteins.fasta
