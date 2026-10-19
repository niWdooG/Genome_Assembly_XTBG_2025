# Quality Check and Genome Assembly Using Illumina, ONT, HiFi, and Hi-C Data

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.14851935.svg)](https://doi.org/10.5281/zenodo.14851935)
[![GitHub Pages](https://img.shields.io/badge/Live-Interactive_Tutorial-2ea44f?logo=github)](https://niwdoog.github.io/Genome_Assembly_XTBG_2025/)
[![Visitors](https://komarev.com/ghpvc/?username=niWdooG-Genome-Assembly-XTBG-2025&label=Visitors&color=0e75b6&style=flat)](https://github.com/niWdooG/Genome_Assembly_XTBG_2025)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

> 📖 **Live Interactive Protocol & Tutorial:**  
> Access the rendered walkthrough with interactive dot plots, FastQC/NanoPlot reports, BUSCO charts, and code blocks at:  
> **[https://niwdoog.github.io/Genome_Assembly_XTBG_2025/](https://niwdoog.github.io/Genome_Assembly_XTBG_2025/)**

---

## Overview

This repository provides practical bioinformatic pipelines developed for the workshop ***Introduction to Bioinformatics and OMICs Data Analysis***, held at Xishuangbanna Tropical Botanical Garden (XTBG) from February 10–14, 2025 (led by Dr. Guillem Ylla). 

The curriculum demonstrates end-to-end processing—from raw read quality assessment through *de novo* assembly, short/long-read error polishing, repeat masking, structural annotation, and comparative synteny[cite: 5]. To ensure fast runtime during practical sessions, analyses focus on a downsized dataset containing Chromosome 4 (ca. 22.2 Mbp) of *Arabidopsis thaliana* using multi-platform sequencing data produced by Wang B et al. (2021)[cite: 5].

---

## Computational Pipeline & Tools

| Workflow Stage | Focus Area | Tools & Packages Used |
| :--- | :--- | :--- |
| **Data Ingestion & Subsampling** | Format conversion, trimming, alignment & read sampling | `fasterq-dump` (sra-tools), `trim_galore`, `cutadapt`, `porechop`, `necat`, `hisat2`, `minimap2`, `samtools`, `seqtk`[cite: 5] |
| **Read Quality Control** | Short- and long-read quality assessment | `FastQC`, `Trim Galore!`, `NanoPlot`[cite: 5] |
| **De Novo Assembly & Polishing** | Long-read assembly, dot-plot validation & hybrid polishing | `Flye`, `D-Genies`, `minimap2`, `yak`, `nextPolish2`, `samtools`, `seqtk`[cite: 5] |
| **Reference-Free Scaffolding** | Chromosome-scale Hi-C scaffolding guidance | `Juicer`, `Juicebox Assembly Tools`[cite: 5] |
| **Transposable Elements** | *De novo* repeat modeling and soft-masking | `RepeatModeler`, `RepeatMasker`[cite: 5] |
| **Structural Annotation** | RNA-Seq mapping, protein evidence integration & transcript extraction | `hisat2`, `samtools`, `BRAKER3`, `AGAT`, `gffread`[cite: 5] |
| **Quality Assessment & Synteny** | Gene completeness, misassembly metrics & collinearity | `BUSCO` (`embryophyta_odb10`), `QUAST`, `D-Genies`, `jcvi`[cite: 5] |

---

## Table of Contents

- **[I] Preface**[cite: 5]
  - In a nutshell (Workshop context, dataset, and downsizing to Chr4)[cite: 5]
  - Learning outcomes[cite: 5]
  - Keywords[cite: 5]
- **[II] Conda & Sequencing Data**[cite: 5]
  - Conda, software, and packages[cite: 5]
  - Downloading raw sequence data (Zenodo archive `14877608`)[cite: 5]
  - Subsampling workflow[cite: 5]
    - [1] Dataset setup (Illumina, RNAseq, Hi-C, HiFi, ONT)[cite: 5]
    - [2] Reference genome download and Chromosome 4 extraction (`awk`, `minimap2`, `hisat2-build`)[cite: 5]
    - [3] Trimming and alignment across data types[cite: 5]
      - Illumina DNA data (`trim_galore`, `hisat2`, `samtools`, `seqtk`)[cite: 5]
      - Illumina RNA data (`fasterq-dump`, `trim_galore`, `hisat2`, `samtools`)[cite: 5]
      - Illumina Hi-C data (`trim_galore`, `hisat2`, `samtools`)[cite: 5]
      - PacBio HiFi data (`cutadapt`, `minimap2`, `samtools`, `seqtk`)[cite: 5]
      - ONT data (`porechop`, `necat correct`, `minimap2`, `samtools`)[cite: 5]
    - [4] Subsampling for the QC chapter (`seqtk`)[cite: 5]
- **[III] Genome Assembly**[cite: 5]
  - Recap: Great Wall analogy and hybrid sequencing rationale[cite: 5]
  - Quality check[cite: 5]
    - Short-Read Sequencing: `FastQC` and `Trim Galore!`[cite: 5]
    - Long-Read Sequencing: `NanoPlot` for PacBio HiFi and ONT reads[cite: 5]
  - Assembly with a reference genome[cite: 5]
    - [1] `Flye` contig assembly[cite: 5]
    - [2] `D-Genies` synthetic similarity dot plots and contig filtering[cite: 5]
    - [3] `NextPolish` (HiFi alignment via `minimap2`, *k*-mer profiling via `yak`, polishing via `nextPolish2`)[cite: 5]
    - [4] Final notes: contig re-orientation (reversing Contig 6) and validation[cite: 5]
  - Assembly without a reference genome (Hi-C scaffolding overview via `Juicer` and `Juicebox`)[cite: 5]
- **[IV] Genome Annotation**[cite: 5]
  - Repeat identification and masking[cite: 5]
    - [1] `RepeatModeler` (`BuildDatabase`, `RepeatModeler`)[cite: 5]
    - [2] `RepeatMasker` (soft-masking with custom repeat library)[cite: 5]
  - Structural annotation[cite: 5]
    - Header cleanup (`sed`) and Viridiplantae protein evidence preparation[cite: 5]
    - RNA-Seq alignment (`hisat2`, `samtools`)[cite: 5]
    - Gene prediction with `BRAKER3`[cite: 5]
    - Annotation statistics and isoform filtering with `AGAT`[cite: 5]
- **[V] Quality Assessment**[cite: 5]
  - `BUSCO` assessment (reference genome vs. assembled genome vs. predicted proteins)[cite: 5]
  - `QUAST` assembly contiguity and misassembly evaluation[cite: 5]
  - `D-Genies` whole-chromosome dot-plot verification[cite: 5]
  - Comparative synteny and collinearity analysis (*Arabidopsis thaliana* vs. *Arabidopsis arenosa* via `jcvi`)[cite: 5]
- **[VI] Software Reference**[cite: 5]
  - Complete list of conda package versions[cite: 5]
- **[VII] Citation**[cite: 5]
