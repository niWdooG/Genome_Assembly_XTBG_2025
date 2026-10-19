# Plant Genome Assembly & Quality Assessment (Illumina, ONT, HiFi, Hi-C)

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.14851935.svg)](https://doi.org/10.5281/zenodo.14851935)
[![GitHub Pages](https://img.shields.io/badge/Live-Interactive_Tutorial-2ea44f?logo=github)](https://niwdoog.github.io/Genome_Assembly_XTBG_2025/)
[![Visitors](https://komarev.com/ghpvc/?username=niWdooG-Genome-Assembly-XTBG-2025&label=Visitors&color=0e75b6&style=flat)](https://github.com/niWdooG/Genome_Assembly_XTBG_2025)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

> 📖 **Live Interactive Protocol & Tutorial:**  
> Access the rendered step-by-step training modules, visual QC outputs, and executable bash scripts at:  
> **[https://niwdoog.github.io/Genome_Assembly_XTBG_2025/](https://niwdoog.github.io/Genome_Assembly_XTBG_2025/)**

---

## Overview

This repository hosts practical materials and reproducible bioinformatic workflows developed for the *"Introduction to Bioinformatics and Omics Data Analysis"* workshop at the Xishuangbanna Tropical Botanical Garden (XTBG), Chinese Academy of Sciences. 

The curriculum covers end-to-end data processing pipelines for plant genome assembly, transitioning from raw short- and long-read quality control to phased contig assembly, Hi-C scaffolding, and genomic completeness benchmarking.

### Sequencing Platforms & Computational Workflow

| Stage | Focus Area | Data Type / Tools |
| :--- | :--- | :--- |
| **I. Read Quality Control** | Ingestion, filtering, and metric profiling | Illumina, ONT, PacBio HiFi (FastQC, fastp, NanoPlot) |
| **II. Genome Profiling** | Genome size, heterozygosity, and repeat fraction | *k*-mer profiling (Jellyfish, GenomeScope 2.0) |
| **III. Contig Assembly** | Graph-based assembly and haplotype phasing | PacBio HiFi / ONT (Hifiasm, Flye, NextDenovo) |
| **IV. Base Polishing** | Residual indel and substitution correction | Short/Long read alignment (NextPolish, Medaka) |
| **V. Scaffolding** | Chromosome-level architecture via chromatin capture | Hi-C conformation capture (YaHS / Juicer / 3D-DNA) |
| **VI. Benchmarking** | Contiguity, completeness, and consensus accuracy | QUAST, BUSCO, Merqury |

---

## Curriculum & Table of Contents

- **[01] Environment Setup & Data Acquisition**
  - Linux HPC and environment management via Conda/Mamba
  - Server hardware recommendations & multi-threading allocation
  - Ingestion of public SRA/ENA sequencing runs
- **[02] Raw Sequencing Data Quality Assessment**
  - Short-read evaluation and adapter trimming
  - Long-read length distributions and mean Q-score filtering
  - Basecalling validation for Oxford Nanopore and PacBio HiFi
- **[03] Pre-Assembly Genome Profiling**
  - Counting *k*-mers from raw Illumina reads
  - Model fitting for ploidy, heterozygosity, and genome size
- **[04] De Novo Contig Assembly**
  - Haplotype-aware assembly using PacBio HiFi data
  - Long-read assembly strategies for ultra-long Nanopore reads
  - Contig error correction and organellar/contaminant screening
- **[05] Chromosome-Scale Hi-C Scaffolding**
  - Alignment of chromatin conformation capture reads
  - Contact matrix generation and scaffolding pipeline execution
  - Manual curation and inversion verification
- **[06] Final Quality Benchmarking & Validation**
  - Assembly continuity assessment ($N50$, $L50$, total length) via QUAST
  - Gene space completeness validation via lineage-specific BUSCO datasets
  - Base-accuracy ($QV$) and phasing evaluation via Merqury

---

## Citation

If you use these materials, training pipelines, or code snippets in your research or teaching curricula, please cite the archived Zenodo release:

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
