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

This repository provides practical bioinformatic pipelines developed for the workshop ***Introduction to Bioinformatics and OMICs Data Analysis***, held at Xishuangbanna Tropical Botanical Garden (XTBG) from February 10-14, 2025 (led by Dr. Guillem Ylla). 

The curriculum demonstrates end-to-end processing from raw read quality assessment through *de novo* assembly, short/long-read error polishing, repeat masking, structural annotation, and comparative synteny. To ensure fast runtime during practical sessions, analyses focus on a downsized dataset containing Chromosome 4 (ca. 22.2 Mbp) of *Arabidopsis thaliana* using multi-platform sequencing data produced by Wang B et al. (2021).

---

## Computational Pipeline & Tools

| Workflow Stage | Focus Area | Tools & Packages Used |
| :--- | :--- | :--- |
| **Data Ingestion & Subsampling** | Format conversion, trimming, alignment & read sampling | `fasterq-dump` (sra-tools), `trim_galore`, `cutadapt`, `porechop`, `necat`, `hisat2`, `minimap2`, `samtools`, `seqtk` |
| **Read Quality Control** | Short- and long-read quality assessment | `FastQC`, `Trim Galore!`, `NanoPlot` |
| **De Novo Assembly & Polishing** | Long-read assembly, dot-plot validation & hybrid polishing | `Flye`, `D-Genies`, `minimap2`, `yak`, `nextPolish2`, `samtools`, `seqtk` |
| **Reference-Free Scaffolding** | Chromosome-scale Hi-C scaffolding guidance | `Juicer`, `Juicebox Assembly Tools` |
| **Transposable Elements** | *De novo* repeat modeling and soft-masking | `RepeatModeler`, `RepeatMasker` |
| **Structural Annotation** | RNA-Seq mapping, protein evidence integration & transcript extraction | `hisat2`, `samtools`, `BRAKER3`, `AGAT`, `gffread` |
| **Quality Assessment & Synteny** | Gene completeness, misassembly metrics & collinearity | `BUSCO` (`embryophyta_odb10`), `QUAST`, `D-Genies`, `jcvi` |

---

## Table of Contents

- **[I] Preface**
  - In a nutshell (Workshop context, dataset, and downsizing to Chr4)
  - Learning outcomes
  - Keywords
- **[II] Conda & Sequencing Data**
  - Conda, software, and packages
  - Downloading raw sequence data (Zenodo archive `14877608`)
  - Subsampling workflow
    - [1] Dataset setup (Illumina, RNAseq, Hi-C, HiFi, ONT)
    - [2] Reference genome download and Chromosome 4 extraction (`awk`, `minimap2`, `hisat2-build`)
    - [3] Trimming and alignment across data types
      - Illumina DNA data (`trim_galore`, `hisat2`, `samtools`, `seqtk`)
      - Illumina RNA data (`fasterq-dump`, `trim_galore`, `hisat2`, `samtools`)
      - Illumina Hi-C data (`trim_galore`, `hisat2`, `samtools`)
      - PacBio HiFi data (`cutadapt`, `minimap2`, `samtools`, `seqtk`)
      - ONT data (`porechop`, `necat correct`, `minimap2`, `samtools`)
    - [4] Subsampling for the QC chapter (`seqtk`)
- **[III] Genome Assembly**
  - Recap: Great Wall analogy and hybrid sequencing rationale
  - Quality check
    - Short-Read Sequencing: `FastQC` and `Trim Galore!`
    - Long-Read Sequencing: `NanoPlot` for PacBio HiFi and ONT reads
  - Assembly with a reference genome
    - [1] `Flye` contig assembly
    - [2] `D-Genies` synthetic similarity dot plots and contig filtering
    - [3] `NextPolish` (HiFi alignment via `minimap2`, *k*-mer profiling via `yak`, polishing via `nextPolish2`)
    - [4] Final notes: contig re-orientation (reversing Contig 6) and validation
  - Assembly without a reference genome (Hi-C scaffolding overview via `Juicer` and `Juicebox`)
- **[IV] Genome Annotation**
  - Repeat identification and masking
    - [1] `RepeatModeler` (`BuildDatabase`, `RepeatModeler`)
    - [2] `RepeatMasker` (soft-masking with custom repeat library)
  - Structural annotation
    - Header cleanup (`sed`) and Viridiplantae protein evidence preparation
    - RNA-Seq alignment (`hisat2`, `samtools`)
    - Gene prediction with `BRAKER3`
    - Annotation statistics and isoform filtering with `AGAT`
- **[V] Quality Assessment**
  - `BUSCO` assessment (reference genome vs. assembled genome vs. predicted proteins)
  - `QUAST` assembly contiguity and misassembly evaluation
  - `D-Genies` whole-chromosome dot-plot verification
  - Comparative synteny and collinearity analysis (*Arabidopsis thaliana* vs. *Arabidopsis arenosa* via `jcvi`)
- **[VI] Software Reference**
- **[VII] Citation**

---

## Citation

If you use or adapt this tutorial in your academic research or teaching curricula, please cite:

```bibtex
@manual{baiakhmetov_genome_assembly_xtbg_2025,
  author       = {Baiakhmetov, Evgenii},
  title        = {Quality check and genome assembly using Illumina, ONT, HiFi, and Hi-C data},
  year         = {2025},
  publisher    = {Zenodo},
  version      = {v1.0.0},
  doi          = {10.5281/zenodo.14851935},
  url          = {[https://doi.org/10.5281/zenodo.14851935](https://doi.org/10.5281/zenodo.14851935)}
}
