# Comparative Protein Motif Analysis Using Python and ExPASy ScanProsite

## Project Overview

This project focuses on identifying protein sequence motifs in two selected protein sequences using Python and ExPASy ScanProsite.

The aim is to compare Python-based motif detection with the web-based ScanProsite tool.

## Selected Protein Sequences

The original protein FASTA file contained 11 protein sequences. Two representative protein sequences were selected for analysis:

| Protein Accession | Length |
|---|---:|
| NP_000475.1 | 770 amino acids |
| NP_001129488.1 | 746 amino acids |

## Selected PROSITE Motifs

Three PROSITE motifs were selected:

| Motif Name | PROSITE Accession | Description | PROSITE Pattern | Python Regex |
|---|---|---|---|---|
| ASN_GLYCOSYLATION | PS00001 | N-glycosylation site | N-{P}-[ST]-{P} | N[^P][ST][^P] |
| CK2_PHOSPHO_SITE | PS00006 | Casein kinase II phosphorylation site | [ST]-x(2)-[DE] | [ST].{2}[DE] |
| PKC_PHOSPHO_SITE | PS00005 | Protein kinase C phosphorylation site | [ST]-x-[RK] | [ST].[RK] |

## Python Motif Detection Results

| Protein | ASN_GLYCOSYLATION | CK2_PHOSPHO_SITE | PKC_PHOSPHO_SITE | Total |
|---|---:|---:|---:|---:|
| NP_000475.1 | 2 | 13 | 7 | 22 |
| NP_001129488.1 | 2 | 12 | 6 | 20 |

Total Python-detected motif hits: **42**

## ScanProsite Results

The same two protein sequences were submitted to ExPASy ScanProsite.

ScanProsite reported:

- 12 hits in 2 sequences
- 6 hits by profiles
- 6 hits by patterns

The pattern hits shown by ScanProsite were:

| Protein | PROSITE Accession | Position | Matched Sequence |
|---|---|---|---|
| NP_000475.1 | PS00319 | 181–188 | GVEFVCCP |
| NP_000475.1 | PS00280 | 319–337 | FfYGGcgnrnnFdteeyC |
| NP_000475.1 | PS00320 | 756–763 | GYENPTYK |
| NP_001129488.1 | PS00319 | 176–183 | GVEFVCCP |
| NP_001129488.1 | PS00280 | 314–332 | FfYGGcgnrnnFdteeyC |
| NP_001129488.1 | PS00320 | 732–739 | GYENPTYK |

## Comparison

| Method | Search Type | Total Hits |
|---|---|---:|
| Python Regex Scan | Raw motif counting | 42 |
| ScanProsite Default Scan | Filtered PROSITE scan | 12 |

## Explanation

Python detected all occurrences of the selected motifs because it counted every exact match to the regular expression patterns.

ScanProsite showed fewer hits because it applies filtering. The selected motifs are common high-frequency motifs and are marked in PROSITE with:

`/SKIP-FLAG=TRUE`

This means ScanProsite may hide or suppress them by default to reduce false-positive results.

## Conclusion

Python-based motif scanning is useful for raw motif counting because it reports every match.

ScanProsite is more conservative because it filters common motifs and reports fewer, more biologically selective hits.

Therefore, both methods are useful but they serve different purposes.
