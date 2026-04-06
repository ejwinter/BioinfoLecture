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

- "the collection, classification, storage, and analysis of biochemical and biological information
  using computers especially as applied to molecular genetics and genomics" — [Merriam-Webster](https://www.merriam-webster.com/dictionary/bioinformatics)

- From writing cloud-scale sequencing pipelines to building clinician-facing UX to curating variant knowledge bases

- One title, a dozen careers: the pipelines engineer, the clinical informatics developer, the data scientist, the visualization engineer...

- Plenty of opportunity to grow and evolve!

---

# This Talk

- An agenda...

---

# My Work

- Lead Software Engineer and Architect — Mayo's Omics Data Platform
  - A data lake and genomics analytics platform for genomic research at scale on Google Cloud Platform.

- Research AI Services Lead — accelerating research discoveries with AI

- Clinical genomics laboratory support *(until recently)*
  - Pipelines, interpretation support software, genetics knowledge management.

*Focused on the efficiency of those who analyze human variation — because the needs of the patient come first.*

---

# Know Your Business!

- Do NOT leave this to "someone else" to do for long.  Dig in and invest.
- Engineers should:
  - Know their business
  - Learn the domain
  - Relate to Customers
  - Love your users
  - Build tools for a **PURPOSE**, something you're **EXCITED** about

- Not all engineers will — but the valuable ones will.

- **AI is your power tool** — domain knowledge is what makes you skilled enough to use it well

- Workers with advanced AI skills earn **56% more** than peers in the same roles — domain depth is what makes those skills stick — [Dallas Fed, 2026](https://www.dallasfed.org/research/economics/2026/0224)

- The floor has risen — **but so has the ceiling** for those who invest in the domain

<!--
Provocative talk title is intentional. The point: engineers who only wait for requirements become interchangeable.

This is actually great news for you. You're entering the field with AI tools that make you 10x more productive than engineers were five years ago. The ones who will struggle are the ones who lean on AI as a crutch without building real understanding. You're here today learning the domain — that already puts you ahead.

AI raises the floor AND the ceiling — you want to be on the ceiling side.
-->

---

# AI and Bioinformatics

- AI has already transformed the field — this is not a prediction

  - **AlphaFold 3** — protein structure and interaction prediction is largely solved
  - **Genomic foundation models** — Evo, Nucleotide Transformer, DNABERT-2, scGPT
  - **LLMs** are entering clinical variant interpretation workflows today
  - **Agentic tools** write and test substantial pipeline code

- What AI still can't do:
  - Tell you if a variant is *clinically significant* for *this patient*
  - Know whether a pipeline result makes *biological sense*
  - Understand why a genetic counselor needs *this* information in *this* workflow
  - Be accountable

- **That's you.** The bioinformatician who understands the science will direct AI — and be worth far more for it.

<!--
Don't shy away from this. Students are thinking about it. Address it directly and honestly.
AI is a power tool. A nail gun doesn't replace a carpenter — it makes a skilled one unstoppable.
The domain knowledge you build is what separates you from a prompt.
-->

---

# The Genome: Scale, Then Simplicity

- **3 billion base pairs** — 500GB of raw data per sample at clinical coverage
  - 100 samples/day in a clinical lab = 50TB of raw data *per day*

- Sequencing that genome? **Getting easier and cheaper every year**
  - Panel (handful of genes) → WES (~20k genes) → WGS (everything)
  - Cost has dropped from $3B (Human Genome Project) to under $1,000 today

- Generating the sequence is the *easy* part
  - **What you do with it is where bioinformatics lives**

<!--
Pause on the scale — let it sink in. This is one person's genome.
Then flip it: the $1,000 genome is now routine. NextGen Sequencing (2008) was the inflection point.
The commoditization of sequencing is *why* the software and analysis problems are so rich right now.
-->

---

# Where the Real Work Lives

- **Sequence analysis** — extracting the signal from the noise at massive scale

- **Quality assessment & control** — because a bad result can harm a patient

- **Interpretation** — turning a list of variants into an answer for a real person

- **Knowledge management** — so every patient benefits from every patient before them

- **Reporting** — communicating complex findings in a way that actually helps clinicians and patients

- **Discovery** — finding the genetic roots of disease, at scale, for the first time in history

- *"The $1,000 genome and the $100,000 analysis"* — this is where the value is. **This is where you come in.**

<div class="label">Schwarze et al. Genet Med 22, 85–94 (2020). https://doi.org/10.1038/s41436-019-0618-7</div>

<!--
Every one of these bullets is a career. Every one of them is unsolved.
You're not entering a crowded field — you're entering one with enormous open problems and not enough people who understand both the biology and the software.
-->

---

# From Chemistry to Data

- A sequencer fragments DNA into billions of short reads (100–250 bp), each sequenced in parallel
  - The instrument produces billions of tiny images — software turns those into strings of A, T, C, G with quality scores
  - The industry is shifting toward long-read sequencing (PacBio) — better for complex regions and structural variants

- *Want to see how it actually works?* [Illumina Sequencing Explained](https://www.youtube.com/watch?v=fCd6B5HRaZ8)

<!--
One wow moment: billions of reads, all in parallel, each one a tiny piece of the puzzle.
The sequencer is essentially a very fancy camera. The hard part is what comes next.
-->

---

# The Assembly Problem

- Imagine shredding millions of copies of a book and reconstructing it from the fragments

- Two approaches:
  - **De-novo assembly** — compare every fragment against every other *(NP-hard territory — used when no reference exists)*
  - **Reference mapping** — align fragments against a known genome *(fast, but misses truly novel variation)*

- From aligned reads, the sample is compared position-by-position to the reference — differences are **variant calls**

- No two callers agree perfectly — the overlap between tools is the confidence zone

<!--
This is a genuine CS problem. Algorithmic trade-offs, data structures, parallelism — it's all here.
The variant calling venn on the next slide makes the uncertainty tangible.
-->

---
layout: image
image: /images/variant_venn.png
---

# No Two Callers Agree

<!--
Source: https://genomemedicine.biomedcentral.com/articles/10.1186/gm432
Different callers (GATK, SAMTools, SOAPsnp, SNVer, GNUMAP) find different variants — the overlap is the confidence zone.
Pipeline selection and management is a real engineering and scientific problem.
-->

---

# The Industry Settled on This

<img src="/images/gatk_pipeline.png" style="width:100%; height:75vh; object-fit:contain; display:block;" />

<!--
You don't need to understand every box. The point is that a decade of research converged into a pipeline that now runs on millions of samples a day.
GATK Best Practices: Raw unmapped reads → Map to reference → Mark duplicates → Recalibrate base quality scores → Analysis-ready BAM → HaplotypeCaller → GVCFs → Joint-call cohort → Filter → Annotate → Evaluate callset.
That's what standardization looks like — and it's open source. The hard problems are upstream and downstream of this.
-->

---

# Variant Types

<img src="/images/variant_types.png" style="width:100%; height:75vh; object-fit:contain; display:block;" />

<!--
SNV, Deletion, Insertion, Tandem Duplication, Interspersed Duplication, Inversion, Translocation, Copy Number Variant.
Each has different detection strategies and clinical significance.
-->

---

# Interpretation

- We now know all the variants the subject has from a reference ... that is the easy part

- Often performed by genetic counselors reviewing literature

- 5 class system: Benign, Likely Benign, **Likely Pathogenic, Pathogenic**, Variant of Unknown Significance (VUS)

- AI is beginning to assist here — LLMs entering clinical variant interpretation workflows today

<!--
The "easy part" is often the domain of the bioinformatician.
Interpretation is performed largely by genetic counselors — but AI is starting to change this.
Ties back to the AI slide: this is one of the hard, human-judgment-heavy problems that AI is now approaching.
-->

---

# Holy Data!

- You have roughly 4 to 5 million SNPs from the human reference genome

- You have about 175 frameshift InDels

- 5% of your genome can be described as a 'structural variant'

- You have hundreds of 'Pathogenic' variants!

**How do you tell the important stuff efficiently?**

---

# Knowledge Management

- Every variant interpreted once should never need to be interpreted from scratch again — the goal is to invest in new discovery, not re-work

- The funnel: **20k+ genes → ~2.5k tied to disease → ~80 actionable today**

- [Jackson Labs CKB](https://ckb.jax.org/) — one of the most important curated knowledge bases in clinical genomics. Explore it!

---
layout: two-cols
---

# User Experience and Visualization

- The greatest opportunity for improvement is here — data is growing exponentially, but the workforce isn't

- Only **~4.7k** certified genetic counselors and **~1.2k** medical geneticists in the U.S.

- Better tools don't just help — they're the only way to scale. **This is where engineers make the biggest difference.**

::right::

<img src="/images/ux_viz.png" style="width:100%;height:100%;object-fit:contain;" />

---

# Predicting Variant Impact

- Algorithms that predict whether a mutation matters — using chemistry, evolutionary conservation, and machine learning

- **Missense prediction** (SIFT, PolyPhen) — does swapping this amino acid break the protein?

- **Splice site prediction** (SpliceAI, MaxEntScan) — does this mutation disrupt how genes are read?

- The frontier: deep learning models are increasingly outperforming classical tools

<!--
These are genuine CS/ML problems. SpliceAI is a deep neural net. AlphaFold solved structure prediction. This field rewards people who understand both algorithms and biology.
-->

---

# Databases That Power It All

- None of this works without massive, shared datasets — bioinformatics runs on open data

- **Reference databases** — dbSNP, 1000 Genomes, HGMD, dbNSFP, and [ClinVar](https://www.ncbi.nlm.nih.gov/clinvar/) — the public archive linking variants to clinical significance

- **Population databases** — how common is this variant across different populations? A variant common in one group may be rare and significant in another

- [gnomAD](https://gnomad.broadinstitute.org/gene/ENSG00000165671?dataset=gnomad_r2_1) — the gold standard for population allele frequencies. Explore it!

---

# GWAS and Biobanking

- What if you could compare millions of genomes to find which variants are linked to disease? That's GWAS.

- The approach: test every variant position across an entire population against a phenotype (e.g. diabetes, heart disease) — a massive statistical sweep

- The catch: millions of simultaneous hypothesis tests means you need extreme significance thresholds (p < 5×10⁻⁸) to avoid false positives — a CS-scale multiple testing problem

- The key insight: the more genomes you bank with phenotype data, the more you can discover — **scale IS the science**
  - UK Biobank: 500k genomes. The discoveries accelerate as the dataset grows.

- A great primer: [nature.com/articles/s43586-021-00056-9](https://www.nature.com/articles/s43586-021-00056-9)

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

- **RNA-Seq** identifies which genes are "turned on" — compare healthy vs. diseased cells to find which genes are misbehaving

- Why this matters as a research edge:
  - The genome is **static** — you're born with it. The transcriptome is **dynamic** — it changes with disease, treatment, time of day, even stress
  - Two patients with the same mutation can have completely different outcomes — transcriptomics helps explain why
  - Drug response: is the therapy actually changing gene expression? RNA-Seq can tell you

- Applications: disease profiling, drug response, developmental biology, single-cell analysis — millions of reads per sample

- Genomics tells you what *could* happen. Transcriptomics tells you what *is* happening.

<!--
This is arguably where the biggest untapped research opportunities are. Genomics has had decades of investment. Transcriptomics is still maturing — tools, pipelines, and interpretation frameworks all need engineering talent.
From a CS perspective — think about the data pipelines, alignment algorithms, and normalization techniques needed to make sense of massive RNA-Seq datasets.
-->

---

# Gene Expression Visualization

<img src="/images/gene_expression.png" style="width:100%; height:75vh; object-fit:contain; display:block;" />

<!--
Volcano plot: statistical significance (-log10 p-value) vs. fold change (logFC).
Blue = downregulated, red = upregulated, grey = not significant.
Highlights genes that are both biologically and statistically significant — the ones worth investigating.
-->

---

# Spatial Transcriptomics

<img src="/images/spatial_transcriptomics.png" style="width:100%; height:55vh; object-fit:contain; display:block;" />

- See what genes are expressed and **where** — "Molecular Cartography" down to single cells on a tissue slide

- Different diseases (e.g. cancers) express different genes in different locations — spatial context changes everything

---

# Workflow Management

- So much bioinformatics has to do with managing pipelines — reproducibility, parallelism, and portability matter enormously

- Manually assembling scripts is error-prone and doesn't scale

- [Nextflow](https://www.nextflow.io/) — the dominant workflow engine in bioinformatics today
  - [nf-core](https://nf-co.re/) — a community-curated collection of production-ready pipelines (including [Sarek](https://github.com/nf-core/sarek) for GATK Best Practices)
  - [Snakemake](https://snakemake.readthedocs.io/) — another strong option, Python-based

- If you learn one tool for bioinformatics infrastructure, make it Nextflow

---

# Genomics in the Cloud

- It costs too much to bring the data to your science. **Your science needs to go to the data.**

- All major cloud providers (Google, AWS, Azure) have heavy investments in genomics infrastructure and public datasets

- The greatest benefits of genomics come at population scale — millions and billions of genomes. Only the cloud makes that possible.

- Get started: [1000 Genomes on GCP](https://cloud.google.com/life-sciences/docs/resources/public-datasets/1000-genomes) — real genomic data you can query today

---

# Learn the Business

- Whatever domain you're in — read the textbooks your users read. You'll be a better engineer for it.

- Remember: AI is your power tool. **Domain knowledge is what makes you skilled enough to use it well.**

- Workers with domain depth + AI fluency earn **56% more** than peers without it

- The floor has risen — but so has the ceiling for those who invest

<!--
This is the callback to the earlier "Know Your Business" slide. Reinforce the message now that they've seen the breadth of the field.
-->

---

# Getting Started: The Science

- Get your hands on real data — [1000 Genomes](http://www.1000genomes.org/data) is free and waiting

- Learn the biology — pick one and go deep:
  - [Genomic Data Science Specialization](https://www.coursera.org/specializations/genomic-data-science) (Coursera)
  - [Bioinformatics Specialization](https://www.coursera.org/specializations/bioinformatics) (Coursera)
  - [Broad Institute courses](https://cmg.broadinstitute.org/course-offering) — from the people who build GATK

- Read the textbooks your users read — even one molecular biology primer will change how you think about the problems

---

# Getting Started: The Engineering

- **Python** — the lingua franca of bioinformatics. Pandas, NumPy, and scikit-learn are your daily tools

- **R** — still strong for statistical genomics and visualization (ggplot2, Bioconductor)

- **Linux and Bash** — you'll live in the terminal. If you're not comfortable yet, get there fast

- **Nextflow** — the pipeline engine the field runs on (you've already seen why)

- **Parallel computing** (SLURM, cloud batch) — genomics workloads are embarrassingly parallel. Learn to exploit that

---

# Learn to Leverage A.I.

- You've seen where AI already is in bioinformatics — now make it part of your daily workflow

- **Use AI to write and test code** — [GitHub Copilot](https://github.com/features/copilot), Claude, Cursor — these are standard tools, not shortcuts

- **Use AI to learn the domain faster** — ask it to explain papers, summarize variant databases, teach you biology

- **But never trust it blindly** — remember, only 1% of developers rely on AI alone. Your judgment is the filter.

- The engineers who thrive will combine **deep domain knowledge with AI fluency** — that's the whole talk in one line

<!--
This loops back to Know Your Business. AI amplifies what you bring. If you bring domain depth, you're unstoppable. If you bring nothing, AI has nothing to amplify.
-->

---

# Your Career Starts Now

- You're extremely lucky if you land your dream job right away — and that's okay. Start somewhere tolerable and grow from there.

- Build in public — get your code on GitHub. Make it something you'd proudly show in an interview.

- Never stop learning — informally, formally (M.S., Ph.D.), or just by building things that excite you

- Transform yourself continually. The job you have in five years probably doesn't exist yet.

---
layout: end
---

# Thank You

[ejwinter@gmail.com](mailto:ejwinter@gmail.com)
