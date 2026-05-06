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
```

---

## 🎯 Selected PROSITE Motifs

Three PROSITE motifs were selected for Python-based motif detection:

| Motif Name | PROSITE Accession | Description | PROSITE Pattern | Python Regex |
|---|---|---|---|---|
| `ASN_GLYCOSYLATION` | `PS00001` | N-glycosylation site | `N-{P}-[ST]-{P}` | `N[^P][ST][^P]` |
| `CK2_PHOSPHO_SITE` | `PS00006` | Casein kinase II phosphorylation site | `[ST]-x(2)-[DE]` | `[ST].{2}[DE]` |
| `PKC_PHOSPHO_SITE` | `PS00005` | Protein kinase C phosphorylation site | `[ST]-x-[RK]` | `[ST].[RK]` |

The official motif definitions were extracted from the downloaded PROSITE database file:

```text
prosite.dat.txt
```

---

## 🧬 PROSITE Pattern Conversion

The PROSITE motif syntax was converted into equivalent Python regular expressions.

| PROSITE Meaning | Python Regex Meaning |
|---|---|
| `{P}` | Any amino acid except proline |
| `[ST]` | Serine or threonine |
| `x` | Any amino acid |
| `x(2)` | Any two amino acids |
| `[DE]` | Aspartic acid or glutamic acid |
| `[RK]` | Arginine or lysine |

Example:

```text
PROSITE pattern: [ST]-x-[RK]
Python regex:    [ST].[RK]
```

This means:

- `S` or `T`
- followed by any amino acid
- followed by `R` or `K`

---

## 🐍 Python Motif Detection Method

Python regular expressions were used to scan both protein sequences.

The script detected:

- Protein accession
- Motif name
- PROSITE accession number
- Start position
- End position
- Matched sequence

A lookahead regular expression was used to allow overlapping motif matches.

---

## 🐍 Python Motif Detection Results

Python detected all occurrences of the selected motifs in both protein sequences.

| Protein | ASN_GLYCOSYLATION | CK2_PHOSPHO_SITE | PKC_PHOSPHO_SITE | Total |
|---|---:|---:|---:|---:|
| `NP_000475.1` | 2 | 13 | 7 | 22 |
| `NP_001129488.1` | 2 | 12 | 6 | 20 |
| **Total** | **4** | **25** | **13** | **42** |

Total Python-detected motif hits:

```text
42 hits
```

---

## 🌐 ExPASy ScanProsite Analysis

The same two protein sequences were submitted to **ExPASy ScanProsite**.

ScanProsite reported:

| Result Type | Number of Hits |
|---|---:|
| Total hits | 12 |
| Hits by profiles | 6 |
| Hits by patterns | 6 |

---

## 🌐 ScanProsite Pattern Hits

The pattern hits shown by ScanProsite were:

| Protein | PROSITE Accession | Position | Matched Sequence |
|---|---|---|---|
| `NP_000475.1` | `PS00319` | 181–188 | `GVEFVCCP` |
| `NP_000475.1` | `PS00280` | 319–337 | `FfYGGcgnrnnFdteeyC` |
| `NP_000475.1` | `PS00320` | 756–763 | `GYENPTYK` |
| `NP_001129488.1` | `PS00319` | 176–183 | `GVEFVCCP` |
| `NP_001129488.1` | `PS00280` | 314–332 | `FfYGGcgnrnnFdteeyC` |
| `NP_001129488.1` | `PS00320` | 732–739 | `GYENPTYK` |

---

## ⚖️ Method Comparison

| Method | Search Type | Target Motifs | Total Hits | Interpretation |
|---|---|---|---:|---|
| Python Regex Scan | Raw motif counting | `PS00001`, `PS00005`, `PS00006` | 42 | Reports every exact motif match |
| ScanProsite Default Scan | Filtered PROSITE scan | Default visible PROSITE hits | 12 | Reports fewer, more biologically selective hits |

---

## 🔍 Why Are the Results Different?

The Python script detected all occurrences of the selected PROSITE motifs because it performed **raw pattern matching**.

However, ScanProsite did not display the same selected motifs in the default result. This is because the selected motifs are common high-frequency motifs and are marked in PROSITE with:

```text
/SKIP-FLAG=TRUE
```

This means ScanProsite may suppress these motifs by default to reduce false-positive results.

Therefore:

- **Python** reports every exact motif match.
- **ScanProsite** applies filtering and reports fewer, more conservative hits.

---

## 🧠 Biological Interpretation

The selected motifs have possible functional importance:

### 1. N-glycosylation site

N-glycosylation motifs may indicate possible glycosylation sites. Glycosylation can affect protein folding, stability, localization, and interactions.

### 2. Casein kinase II phosphorylation site

CK2 phosphorylation motifs may indicate possible regulatory phosphorylation sites. Phosphorylation can affect protein activity, signaling, and protein-protein interactions.

### 3. Protein kinase C phosphorylation site

PKC phosphorylation motifs may indicate possible kinase regulation. These motifs are important because phosphorylation is a common post-translational modification involved in cell signaling.

However, motif detection alone does not experimentally confirm that these modifications actually occur. The results should be interpreted as **predicted motif sites**.

---

## ✅ Conclusion

Python-based motif scanning is useful for **transparent raw motif counting** because it reports every match to the selected regular expression patterns.

ScanProsite is more conservative because it applies biological filtering and may suppress common high-frequency motifs. Therefore, ScanProsite is more useful for **biological interpretation**, while Python is better for **customizable and reproducible motif counting**.

Overall, both methods are complementary:

> Python gives full control over motif detection, while ScanProsite provides curated and filtered PROSITE-based results.

---

## 📁 Repository Files

| File | Description |
|---|---|
| `README.md` | Project explanation |
| `motif_analysis.ipynb` | Main Python notebook |
| `selected_two_proteins.fasta` | FASTA file containing the two selected proteins |
| `prosite.dat.txt` | Downloaded PROSITE database file |
| `motif_count_table.csv` | Python motif count results |
| `motif_positions_table.csv` | Motif positions and matched sequences |

---

## 🛠️ Tools Used

- Python
- Regular expressions
- Pandas
- Biopython
- ExPASy PROSITE
- ExPASy ScanProsite
- Google Colab
- GitHub

---

## 👩‍💻 Author

This project was prepared as part of a bioinformatics motif analysis study.```text
selected_two_proteins.fasta
