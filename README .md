#  Comparative Protein Motif Analysis
### Using Python and ExPASy ScanProsite

![Python](https://img.shields.io/badge/Python-3.x-blue?style=flat-square&logo=python&logoColor=white)
![Bioinformatics](https://img.shields.io/badge/Field-Bioinformatics-teal?style=flat-square)
![ExPASy](https://img.shields.io/badge/Tool-ExPASy%20ScanProsite-orange?style=flat-square)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen?style=flat-square)

---

## Project Overview

This project identifies **protein sequence motifs** in two selected protein sequences using two complementary approaches:

-  **Python** — regex-based motif scanning for exhaustive hit detection
-  **ExPASy ScanProsite** — web-based, biologically filtered motif scanning

The goal is to compare both methods, understand their differences, and evaluate their use cases in protein functional annotation.

---

## Selected Protein Sequences

Two representative sequences were selected from an original FASTA file containing **11 protein sequences**.

| Protein Accession | Length |
|---|---|
| `NP_000475.1` | 770 amino acids |
| `NP_001129488.1` | 746 amino acids |

---

##  Selected PROSITE Motifs

Three PROSITE motifs were chosen for analysis:

| Motif Name | PROSITE Accession | Description | PROSITE Pattern | Python Regex |
|---|---|---|---|---|
| `ASN_GLYCOSYLATION` | PS00001 | N-glycosylation site | `N-{P}-[ST]-{P}` | `N[^P][ST][^P]` |
| `CK2_PHOSPHO_SITE` | PS00006 | Casein kinase II phosphorylation site | `[ST]-x(2)-[DE]` | `[ST].{2}[DE]` |
| `PKC_PHOSPHO_SITE` | PS00005 | Protein kinase C phosphorylation site | `[ST]-x-[RK]` | `[ST].[RK]` |

---

##  Python Motif Detection Results

Python scanned both sequences using regular expressions, reporting **every exact pattern match**.

| Protein | ASN_GLYCOSYLATION | CK2_PHOSPHO_SITE | PKC_PHOSPHO_SITE | Total |
|---|:---:|:---:|:---:|:---:|
| `NP_000475.1` | 2 | 13 | 7 | **22** |
| `NP_001129488.1` | 2 | 12 | 6 | **20** |
| **Total** | **4** | **25** | **13** | **42** |

> **Total Python-detected motif hits: 42**

---

## ScanProsite Results

The same two sequences were submitted to [ExPASy ScanProsite](https://prosite.expasy.org/scanprosite/).

**Summary:**
-  12 hits across 2 sequences
- 6 hits by **profiles**
- 6 hits by **patterns**

### Pattern Hits Detail

| Protein | PROSITE Accession | Position | Matched Sequence |
|---|---|---|---|
| `NP_000475.1` | PS00319 | 181–188 | `GVEFVCCP` |
| `NP_000475.1` | PS00280 | 319–337 | `FfYGGcgnrnnFdteeyC` |
| `NP_000475.1` | PS00320 | 756–763 | `GYENPTYK` |
| `NP_001129488.1` | PS00319 | 176–183 | `GVEFVCCP` |
| `NP_001129488.1` | PS00280 | 314–332 | `FfYGGcgnrnnFdteeyC` |
| `NP_001129488.1` | PS00320 | 732–739 | `GYENPTYK` |

---

## Method Comparison

| Method | Search Type | Total Hits |
|---|---|:---:|
|  Python Regex Scan | Raw motif counting (all matches) | **42** |
|  ScanProsite Default Scan | Filtered PROSITE scan | **12** |

### Why the difference?

Python detects **all occurrences** of the selected motifs because it counts every exact regex match.

ScanProsite returns **fewer hits** because it applies biological filtering. The three motifs selected (`ASN_GLYCOSYLATION`, `CK2_PHOSPHO_SITE`, `PKC_PHOSPHO_SITE`) are common, high-frequency motifs marked in the PROSITE database with:

```
/SKIP-FLAG=TRUE
```

This flag causes ScanProsite to **suppress or hide** these motifs by default to reduce false-positive results in functional annotation.

---

## Conclusion

| Tool | Best For |
|---|---|
| **Python regex scanning** | Raw motif counting, exhaustive detection, custom pipelines |
|  **ScanProsite** | Biologically selective hits, functional annotation, reduced false positives |

> Both methods are valid and complementary. Python is ideal for **exploring all possible matches**, while ScanProsite is better suited for **biologically meaningful annotation**. The right tool depends on the research goal.

---

##  Tools & Resources

- [ExPASy ScanProsite](https://prosite.expasy.org/scanprosite/) — Web-based motif scanning
- [PROSITE Database](https://prosite.expasy.org/) — Protein domains and functional sites
- [NCBI Protein](https://www.ncbi.nlm.nih.gov/protein/) — Protein sequence source
- Python `re` module — Regular expression-based motif detection

---

*Bioinformatics project — Protein motif analysis and method comparison*
