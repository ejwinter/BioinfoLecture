# Bioinformatics, Genomics and Beyond

A lecture presentation by **Eric Winter M.S.** delivered at Winona State University, April 2026.

Built with [Slidev](https://sli.dev/).

## Overview

This talk introduces software engineering students to the field of bioinformatics and genomic medicine — covering the science, the tooling, and practical career advice for breaking into the field.

## Topics Covered

### The Science
- What bioinformatics is and why it matters
- The human genome: scale, cost, and the sequencing revolution
- Next-Generation Sequencing (NGS) and the emerging shift to long-read sequencing
- The genomics pipeline: sample prep → sequencing → mapping → variant calling → interpretation
- Variant types: SNVs, InDels, structural variants, copy number variants
- Variant interpretation: the 5-class pathogenicity system and the "$1,000 genome, $100,000 analysis" problem
- Population and reference databases (dbSNP, gnomAD, HGMD, 1000 Genomes)
- Missense and splice site prediction tools

### Beyond the Genome
- Transcriptomics and RNA-Seq: measuring gene expression
- Spatial transcriptomics: "molecular cartography" at the tissue and single-cell level
- The broader -ome landscape: transcriptome, microbiome, epigenome, proteome
- Genome-Wide Association Studies (GWAS) and biobanking

### Engineering in Practice
- Workflow management with Nextflow and GATK Best Practices pipelines
- Genomics in the cloud (Google Cloud Platform)
- Knowledge management: avoiding reinterpretation, actionable gene sets
- UX and visualization as the greatest opportunity for impact

### Career Advice
- Know your business domain — engineers who understand the science are irreplaceable
- How AI (AlphaFold, genomic foundation models, agentic coding tools) has already transformed the field
- Getting started: FASTQ/BAM/VCF hands-on practice, GATK, Coursera/Udemy resources
- Learn Linux, Bash, Python (Pandas), and R
- Embrace data science and Jupyter for reproducible research
- Building a career: first jobs, continuous transformation, and putting code on GitHub

## Running the Presentation

```bash
npm install
npm run dev
```

Then open [http://localhost:3030](http://localhost:3030) in your browser.

## Building / Exporting

```bash
# Static site
npm run build

# PDF export
npm run export
```

## Author

Eric Winter M.S. — [ejwinter@gmail.com](mailto:ejwinter@gmail.com)
