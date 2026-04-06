---
theme: default
title: Bioinformatics, Genomics and Beyond
author: Eric Winter M.S.
date: April 2026
highlighter: shiki
lineNumbers: false
drawings:
  persist: false
transition: slide-left
mdc: true
---

# Bioinformatics,<br>Genomics and Beyond

<p>Eric Winter M.S. &nbsp;|&nbsp; Winona State University &nbsp;|&nbsp; April 2026</p>

<!--
Welcome slide — QR code links to slide deck URL once deployed.
-->

---

# "Bioinformatics"<br>An Expansive Definition

- "the science of collecting and analyzing complex biological data such as genetic codes"

- "The use of computer science, mathematics, and information theory to **organize** and **analyze** complex biological data, especially genetic data."

---

# This Talk

- Importance of knowing your business

- Genomic Medicine and Research

- Tips to excel as you start and drive your career

---

# My Work

- Lead Software Engineer and Architect on Mayo's Omics Data Platform
  - A data lake and genomics analytics platform hosted on Google Cloud Platform.

- Until recently, Support of clinical genomics laboratory
  - Pipelines, interpretation support software, genetics knowledge management.

- Efficiency and effectiveness of my customers in analyzing human variation.

- The needs of the patient come first.

---

# Know Your Business Domain!

- [vimeo.com/74437772](http://vimeo.com/74437772) — *"First kill the product owners."*

- Engineers should:
  - Know their business
  - Learn the domain
  - Relate to Customers
  - Love your users
  - Build tools for a **PURPOSE**, something you're **EXCITED** about

- Not all engineers will — but the valuable ones will.

<!--
Provocative talk title is intentional. The point: engineers who only wait for requirements become interchangeable.
The engineers who refuse to learn the domain will be the first ones AI replaces.
-->

---

# The Genome

- 3 billion base pairs

- 24GB in ASCII for raw sequence
  - \>10x coverage plus quality data — about 500GB per sample.

<!--
Good place to pause and let the scale sink in. This is one person's genome.
At 100 samples a day in a clinical lab, that's 50TB of raw data per day.
-->

---
layout: image
image: /images/seq_cost.png
---

# Sequencing...<br>Easy Stuff Getting Cheaper

<!--
Key transition point: 2008 NextGen Sequencing (NGS) hit — also remapping of the genome became dominant before that; de-novo assembly was needed before.
Panel Tests: 1 to a few hundred genes.
Whole Exome Sequencing (WES): all genes ~2k genes.
Whole Genomic Sequencing (WGS): the whole thing.
-->

---

# The Hard Stuff

- **Sequence analysis** — ways to look at raw sequencing data that highlight **meaningful** data.

- **Quality assessment & control** for sequencing workflows and samples.

- **Interpretation** of the impact variation has on gene expression and function.

- **Knowledge management** — minimize time spent re-interpreting information at individual, organizational, and global levels.

- **Reporting** of clinical data in a way meaningful to patients and the public.

- **Discovery** of new variation-phenotype (e.g. disease) associations.

- Clinical interpretation in particular can be lengthy and costly — "the $1,000 genome and the $100,000 analysis."

<div class="label">Schwarze et al. Genet Med 22, 85–94 (2020). https://doi.org/10.1038/s41436-019-0618-7</div>

---

# NextGen Sequencing

- Break large problems into millions of small problems

- 100 – 250 bp sequences all sequenced in parallel

- Alignment among fragments or to a reference sequence

---

# Basic Pipeline Steps

- Sample Prep
- Sequencing
- Assembly / Mapping
- Variant Detection
- Quality Assessment
- Interpretation
- Knowledge Management

---

# Instruments

- Chemistry: DNA is collected, fragmented, and amplified by PCR

- Instrument produces billions of tiny bitmap images (Illumina, Roche 454, Life Technologies IonTorrent)
  - [Illumina Sequencing Explained](https://www.youtube.com/watch?v=fCd6B5HRaZ8)

- Software converts images to FASTQ (or similar) files
  - [maq.sourceforge.net/fastq.shtml](http://maq.sourceforge.net/fastq.shtml)

- The industry is shifting rapidly toward long-read sequencing (LRS) — led by PacBio.
  - LRS greatly improves sequencing of high repeat areas and structural variant discovery.

---

# Assembly and Mapping

- FASTQ files consist of billions of short fragments (reads) of 100–250 bp (typically)

- De-novo assembly aligns each fragment against all others (time **CONSUMING!!!**)

- Mapping assembles them against a standard reference genome (e.g. hg19)

- BAM files are the result

- [SAM v1 Spec](https://samtools.github.io/hts-specs/SAMv1.pdf)

<!--
Show the difference between assembly and mapping on a whiteboard.
Show a BAM file in Alamut — nicely lined up pileups. Note that quality scores of each base are considered in the alignment.
-->

---
layout: image
image: /images/variant_venn.png
---

# The Art of Variant Calling

<!--
Source: https://genomemedicine.biomedcentral.com/articles/10.1186/gm432
Highlight the importance of selecting and carefully managing sequencing and processing pipelines.
Different callers (GATK, SAMTools, SOAPsnp, SNVer, GNUMAP) find different variants — the overlap is the confidence zone.
-->

---

# Variant Calling

- The sample genome (as reflected in the BAM file) is compared to a reference sequence at each position

- A variance from the reference is called when there is enough high-quality data at that position

- [VCF](https://en.wikipedia.org/wiki/Variant_Call_Format) (variant call file) format is the standard

- A really good deep dive on variant calling strategies:
  - [youtube.com/watch?v=zO9WCOaq3aQ](https://www.youtube.com/watch?v=zO9WCOaq3aQ)

<!--
Show a raw VCF file and then show a variant in Alamut and what it looks like compared to the pileup.
-->

---
layout: image
image: /images/gatk_pipeline.png
---

# OK, a Bit More Complicated

<!--
100x / 1000x samples a day!
GATK Best Practices: Raw unmapped reads → Map to reference → Mark duplicates → Recalibrate base quality scores → Analysis-ready BAM → HaplotypeCaller → GVCFs → Joint-call cohort → Filter → Annotate → Evaluate callset.
-->

---
layout: image
image: /images/variant_types.png
---

# Variant Types

<!--
SNV, Deletion, Insertion, Tandem Duplication, Interspersed Duplication, Inversion, Translocation, Copy Number Variant.
Each has different detection strategies and clinical significance.
-->

---

# Interpretation

- We now know all the variants the subject has from a reference ... that is the easy part

- Often performed by genetic counselors reviewing literature

- 5 class system: Benign, Likely Benign, Likely Deleterious, Deleterious, Variant of Unknown Significance (VUS)

<!--
The "easy part" is often the domain of the bioinformatician.
Interpretation is performed largely by genetic counselors.
-->

---

# Holy Data!

- You have roughly 4 to 5 million SNPs from the human reference genome

- You have about 175 frameshift InDels

- 5% of your genome can be described as a 'structural variant'

- You have hundreds of 'Pathogenic' variants!

- How do you tell the important stuff efficiently?

---

# Knowledge Management

- Effectively collecting and exposing genetic information once it is collected — to avoid reinterpretation and invest more in new investigation.

- Over 20k genes, 2.5k tied to disease, ~80 are 'actionable'

- [Jackson Labs CKB](https://ckb.jax.org/)

---
layout: two-cols
---

# User Experience and Visualization

- The greatest opportunity for improvement is here

- There are only ~4.7k certified genetic counselors in the U.S. and ~1.2k medical geneticists.

- We need to make them more efficient by creating great experiences.

::right::

<img src="/images/ux_viz.png" style="max-height:55vh;margin-top:2rem;" />

---

# Missense Prediction

- Sift, Polyphen, AGVGD, ...

- These look at the amino acid change and either examine chemistry or query reference databases (e.g. SwissProt) to assess what the effects of the mutation could be.

<!--
Show in Alamut.
-->

---

# Splice Site Prediction

- SpliceAI, NNSplice, Human Splicing Finder, GeneSplicer, MaxEntScan

- These look at the regions around the exon start and stop regions — determining if the mutation could affect transcription.

<!--
Show in Alamut.
-->

---

# Reference Databases

- dbSNP
- Exome Server
- 1000 Genomes
- HGMD
- dbNSFP

---

# Population Databases

- It is key to find out how variation is observed within different populations.

- gnomAD
  - [gnomad.broadinstitute.org](https://gnomad.broadinstitute.org/gene/ENSG00000165671?dataset=gnomad_r2_1)

- A good review of population databases
  - [arxiv.org/pdf/2107.11458.pdf](https://arxiv.org/pdf/2107.11458.pdf)

---
layout: two-cols
---

# Genome Wide Association Studies (GWAS) and Biobanking

- Taking hundreds of thousands to millions of whole genomes along with phenotypic information and looking for correlations.

- Stresses the importance of banking **MANY** genomes along with phenotype information into a repository.

- A great primer: [nature.com/articles/s43586-021-00056-9](https://www.nature.com/articles/s43586-021-00056-9)

::right::

<img src="/images/gwas.png" style="max-height:55vh;margin-top:2rem;" />

---

# So Many More -Omes

- **Transcriptome** — What mRNA is floating around, meaning some level of expression?

- **Microbiome** — What microorganisms are influencing my phenotype/genotype?

- **Epigenome** — How is my DNA expression being up/down regulated by the environment?

- **Proteome** — What proteins are actually available in my cells? In what form?

- ...Genomes are easy

---

# Transcriptomics

- DNA is just your genetic blueprint. RNA is your DNA responding to the environment and taking action.

- RNA-Seq identifies which genes are 'turned on' in the sample.

- RNA-Seq: key technology for measuring gene expression

- Applications: disease profiling, drug response, developmental biology

- Big data meets biology: millions of reads per sample.

<!--
So far we've focused on DNA — the blueprint. Transcriptomics takes us one step forward: it looks at which parts of the blueprint are actively being used at any given moment.
RNA sequencing gives a readout of everything a cell is expressing at a moment in time.
Why powerful? By comparing expression between healthy and diseased cells, we can identify which genes are misbehaving.
From a CS perspective — think about the data pipelines, alignment algorithms, and normalization techniques needed to make sense of massive RNA-Seq datasets.
-->

---
layout: image
image: /images/gene_expression.png
---

# Gene Expression Visualization

<!--
MD plot: mean expression vs. log fold change between conditions.
Volcano plot: statistical significance vs. fold change — highlights genes that are both biologically and statistically significant.
-->

---
layout: two-cols
---

# Spatial Transcriptomics

- Amazing culmination of transcriptomics — focusing on specific tissues or even single cells on a microscope slide. See what genes are expressed and **where**! "Molecular Cartography."

- Different diseases (e.g. cancers) express different genes or splice variants of genes.

::right::

<img src="/images/spatial_transcriptomics.png" style="max-height:55vh;margin-top:1rem;" />

<div class="label">vizgen.com — MERSCOPE spatial transcriptomics platform</div>

---

# Workflow Management

- So much bioinformatics has to do with managing pipelines

- Manually assembling scripts is error-prone and requires too much specialist talent.

- Workflow engines are a great way to go.

- [Nextflow](https://www.nextflow.io/) — many are moving to this engine.
  - [GATK Best Practices Nextflow Pipeline](https://github.com/nf-core/sarek)

---

# Genomics in the Cloud

**Why?**

- Off-load infrastructure costs.

- Leverage tools and infrastructure (including security) provided by Google, Amazon, Microsoft.

- Institutional and/or Global scaling.
  - We will only see the greatest benefits of genomics when we have millions and billions of genomes for discovery.
  - It costs too much to bring the data to your science. **Your science needs to go to the data.**

---

# Genomics in the Cloud

- Google Cloud has heavy investments in Genomics.
  - [cloud.google.com](https://cloud.google.com/)

- Accessing 1000 Genomes:
  - [cloud.google.com/life-sciences/docs/resources/public-datasets/1000-genomes](https://cloud.google.com/life-sciences/docs/resources/public-datasets/1000-genomes)

---

# GATK Reference Workflow on GCP

- [cloud.google.com/architecture/genomic-data-processing-reference-architecture](https://cloud.google.com/architecture/genomic-data-processing-reference-architecture)

- Grab some FASTQ files and do some bioinformatics!

---
layout: image
image: /images/learn_business.png
---

# Learn the Business

<!--
Three books: how to run a pizza shop, Molecular Biology of the Cell, Principles of Corporate Finance.
The point: whatever domain you're in, read the textbooks your users read. You'll be a better engineer for it.
-->

---

# Genomics Courses

- [Genetics and Next Generation Sequencing for Bioinformatics](https://www.udemy.com/course/genetics-and-next-generation-sequencing-for-bioinformatics/) — Udemy

- [cmg.broadinstitute.org/course-offering](https://cmg.broadinstitute.org/course-offering) (Broad Institute)
  - [youtube.com/watch?v=VqrEtABxvhY](https://www.youtube.com/watch?v=VqrEtABxvhY) (Rehm)

- [Genomics: Decoding the Universal Language of Life](https://www.coursera.org/learn/genomics-research) (Coursera)

- [DNA Decoded](https://www.coursera.org/learn/dna-decoded) (Coursera)

- [From Disease to Genes and Back](https://www.coursera.org/learn/disease-genes) (Coursera)

---
layout: two-cols
---

# Getting Started: Bioinformatics

- Get some actual genomics data
  - FastQ, BAM, VCF files
  - [1000genomes.org/data](http://www.1000genomes.org/data)

- Get GATK 'Genome Analysis ToolKit'

- [Genomic Data Science Specialization (Coursera)](https://www.coursera.org/specializations/genomic-data-science)

- [Bioinformatics Specialization (Coursera)](https://www.coursera.org/specializations/bioinformatics)

::right::

<img src="/images/getting_started_bio.png" style="max-height:55vh;margin-top:1rem;" />

---
layout: two-cols
---

# Getting Started: Development

- Care about your craft!
  - Software Craftsmanship
  - Clean Coder / Clean Code
  - Unit Testing!

::right::

<img src="/images/getting_started_dev.png" style="max-height:55vh;margin-top:1rem;" />

---

# Learn Linux and Bash!!!

- Install Linux on a VM, use it often

- Windows Subsystem for Linux

- Mac OS X (already there)

- [Bash Beginners Guide](http://www.tldp.org/LDP/Bash-Beginners-Guide/html/Bash-Beginners-Guide.html)

- [Advanced Bash Scripting](http://www.tldp.org/LDP/abs/html/)

- **A+**: Also work on parallel computing (e.g. Open Grid Engine, SLURM)

---

# Learn a More Structured Scripting

- Python for overall programming in Bioinformatics
  - Pandas is a powerful data analysis library
  - [Pandas for Biologists](https://www.youtube.com/watch?v=R-PdWANSv0E)

- R for many data science needs — though Pandas has stolen much of the thunder.

---
layout: two-cols
---

# Embrace Data

- [Data Science for Bioinformatics](https://www.youtube.com/c/dataprofessor)

- Jupyter for reproducible research
  - [Genomic data visualization in Jupyter](https://www.youtube.com/watch?v=VqrEtABxvhY)

::right::

<img src="/images/data_science.png" style="max-height:55vh;margin-top:1rem;" />

---

# Learn to Leverage A.I.

- AI has already transformed how bioinformatics is built and practiced — this is no longer a prediction.

- **AI in genomics today:**
  - AlphaFold 3 — protein structure/interaction prediction is largely solved
  - Genomic foundation models: Evo, Nucleotide Transformer, DNABERT-2, scGPT, Geneformer
  - LLM-assisted variant interpretation is now entering clinical workflows
  - Agentic coding tools (Copilot, Claude, Cursor) write and test substantial pipeline code

- Learn to use AI as a force multiplier:
  - [GitHub Copilot](https://github.com/features/copilot)
  - [Build Custom Bioinformatics Tools in No Time With ChatGPT](https://www.youtube.com/watch?v=xX0jJGkDV3o)

- The floor for what a junior bioinformatician needs to bring has risen — **domain depth and judgment are the defense**.

<!--
When I last gave this talk, I said "AI will change work very soon." That ship has sailed.
The engineers who survive and thrive are the ones who combine deep domain knowledge with AI fluency.
This loops back to slide 5: Know Your Business Domain is more important now, not less.
-->

---

# Getting Started: The First Gig

- Look at the job openings

- You're extremely lucky if you get the job you want right away

- Decide where you can get started — something tolerable but perhaps not perfect

- Get ready to transform yourself and your jobs continually.

---

# Transform Yourself and Career

- Learn something outside of school/work

- Continue your education informally and perhaps formally (M.S., Ph.D.)

- Apply it! Start writing code.

- Get that code out there (GitHub)

- Make your code something you can share proudly in interviews

---
layout: end
---

# Thank You

[ejwinter@gmail.com](mailto:ejwinter@gmail.com)
