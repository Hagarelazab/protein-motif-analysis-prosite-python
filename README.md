# Comparative Protein Motif Analysis Using Python and PROSITE

![Python](https://img.shields.io/badge/Python-3.x-blue)
![Biopython](https://img.shields.io/badge/Biopython-Sequence%20Analysis-green)
![PROSITE](https://img.shields.io/badge/Database-PROSITE-orange)
![ScanProsite](https://img.shields.io/badge/Tool-ScanProsite-red)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)

## Overview

This project performs a comparative protein motif analysis using two complementary approaches:

1. **Custom Python regular-expression scanning**
2. **ExPASy ScanProsite**

The analysis investigates how direct sequence-pattern detection differs from biologically filtered PROSITE annotation.

Two representative protein sequences were selected from an original FASTA dataset containing 11 protein sequences. Three PROSITE motifs were then searched using Python regular expressions, and the results were compared with ScanProsite output.

The project demonstrates an important bioinformatics principle:

> A sequence-pattern match is not necessarily equivalent to a biologically meaningful functional-site annotation.

---

## Objectives

The main objectives of this project were to:

- Parse protein sequences from FASTA format using Biopython.
- Select representative protein sequences for detailed analysis.
- Use defined PROSITE motifs for sequence scanning.
- Translate PROSITE patterns into Python-compatible regular expressions.
- Identify motif positions directly from amino-acid sequences.
- Quantify motif frequencies across the selected proteins.
- Compare raw Python motif detection with ExPASy ScanProsite.
- Investigate why the two approaches produce different numbers of reported hits.

---

## Analysis Workflow

```text
Protein FASTA dataset
        |
        v
Sequence parsing with Biopython
        |
        v
Selection of two protein sequences
        |
        v
Selection of three PROSITE motifs
        |
        +-------------------------+
        |                         |
        v                         v
Python regex scanning       ExPASy ScanProsite
        |                         |
        v                         v
Raw motif matches        Filtered PROSITE annotations
        |                         |
        +------------+------------+
                     |
                     v
             Method comparison
