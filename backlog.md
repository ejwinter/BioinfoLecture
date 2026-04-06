# Presentation Improvement Backlog

## High Priority

### AI Slide (slide 41) — Substantially Outdated
The original said "A.I. will change almost all work very soon." That was 2023 language.
Current state as of 2026:
- AlphaFold 3 has largely solved protein structure/interaction prediction
- Genomic foundation models (Evo, Nucleotide Transformer, DNABERT-2, scGPT, Geneformer) are in active use
- LLM-assisted variant interpretation is entering clinical workflows
- Agentic coding tools write and test substantial pipeline code
- Junior engineer hiring has dropped noticeably in bioinfo

**Suggested fix:** Expand to 2-3 slides: (1) What AI can do in genomics now, (2) What it means for the job market students are entering, (3) How to stay valuable = domain depth + judgment. Tie back to "Know Your Business Domain."

---

### "Know Your Business Domain" (slide 5) — Good, Make It Stronger
This is the strongest, most opinionated slide. Currently it's bullets. It deserves a story.

**Suggested fix:**
- Add one concrete anecdote from your own work: a specific decision you made that required genomics domain knowledge and that a generic engineer would have missed.
- Sharpen the closing line: "The valuable ones will" → "The engineers who refuse to learn the domain will be the first ones AI replaces." (Creates a bridge to the AI section.)
- The Vimeo URL "First kill the product owners" — add a one-line paraphrase on the slide so the punchline lands for people not clicking in the moment.

---

### Missing Slide: "What the Work Actually Looks Like"
The deck covers technology and pipelines thoroughly but doesn't show students what the job *feels like*.

**Suggested new slide (replace a lighter technical slide):**
- Who you collaborate with daily: geneticists, counselors, lab techs, clinicians, PMs
- What a typical week looks like
- What goes wrong: failed runs, ambiguous variants, pipeline drift, on-call
- The emotional stakes: the patient is at the end of this pipeline (cash out "needs of the patient come first" from slide 4 with a real story)
- The honest reality: much of the job is data wrangling and fighting file formats

---

## Medium Priority

### Sequencing Cost Chart (slide 7) — Outdated
The chart cuts off at 2021. Long-read sequencing costs have collapsed since then.

**Suggested fix:**
- Update chart from NHGRI (https://www.genome.gov/about-genomics/fact-sheets/Sequencing-Human-Genome-cost)
- Add a note on competitive landscape: Ultima, Element Bio, MGI have cracked Illumina's near-monopoly — significant for anyone entering the field

---

### Variant Calling Venn Diagram (slide 13) — From 2012
The Venn diagram comparing GATK, SAMTools, SOAPsnp, etc. is from a 2012 paper. DeepVariant and ML-based callers have substantially changed this picture.

**Suggested fix:**
- Update or replace with a more recent comparison
- Keep the point (pipeline selection matters) but modernize the illustration
- Could add a note that DeepVariant/ML callers have different trade-off profiles than the classic heuristic callers

---

### User Experience (slide 20) — Numbers Likely Outdated
"~4.7k certified genetic counselors and ~1.2k medical geneticists" — worth verifying current numbers.

Also: this slide should note that AI is now directly attacking this bottleneck (LLM-assisted interpretation), which creates urgency for the tooling work you're describing.

---

### Deck Length — 44 Slides is Tight for 45-60 Minutes
The technical middle (slides 9-13 on sequencing mechanics) is dense and could be consolidated without losing the arc. This would create room for the new AI/real-world content.

**Suggested consolidation candidates:**
- Slides 9 (NextGen Sequencing) + 10 (Basic Pipeline Steps) could merge
- Slides 11 (Instruments) + 12 (Assembly and Mapping) could merge
- Slides 31 + 32 (both Genomics in the Cloud) could merge

---

### Structure — AI Content Buried at Slide 41
If AI is now central to the real-world picture for students, it shouldn't appear as a late "oh by the way."

**Suggested structural change:** Move AI/real-world content earlier, woven into the "Know Your Business" thesis rather than in the career tips section. The argument is: here's the domain (genomics), here's why knowing it matters (AI is coming for the parts you don't know), here's how to prepare.

---

## Lower Priority / Polish

### Slidev Migration Improvements
- Add Mermaid diagram for the Basic Pipeline Steps instead of plain bullets
- Replace the GATK pipeline static image with a Mermaid flowchart (editable, searchable)
- Add syntax-highlighted code examples showing what a VCF or FASTQ file actually looks like
- Consider adding a live Mermaid diagram for variant types instead of the static image
- Add slide transitions: section breaks could use a different transition

### Title Slide — Date Needs Updating
Currently shows April 15, 2025. Update to current presentation date.

### Speaker Notes
Several slides have "Show in Alamut" notes that assume a live demo environment. Consider whether the demos are still happening and if so, what the fallback is if Alamut isn't available.

### "Learn the Business" Slide (slide 34)
The three-book visual (pizza shop, Molecular Biology of the Cell, Corporate Finance) is a great, memorable slide. Keep it. Consider updating to current editions.

### Reference Databases (slide 23)
ClinVar is notably absent from the reference databases list — it's arguably the most important clinical variant database. Worth adding alongside HGMD, dbSNP, gnomAD, etc.

---

## Ideas for New Slides

### "A Day in the Life" / "What the Job Actually Looks Like"
See High Priority above.

### "AI in Genomics: The State of Play (2026)"
Concrete, current examples of AI being used in the field:
- AlphaFold 3 protein/interaction prediction
- scGPT / Geneformer for single-cell analysis
- Fabric Genomics / other LLM-assisted interpretation tools
- Copilot/Claude for pipeline development
- Where it's still failing (hallucinations in variant interpretation, data privacy constraints)

### "The Bottleneck Problem"
The deck mentions counselor/geneticist scarcity but doesn't dwell on it. A dedicated slide on the supply/demand gap in clinical genomics would motivate both the UX work and the AI conversation.

### "What Makes a Great Bioinformatician" (closing section)
Currently the career advice is scattered across several slides. A single strong closing slide summarizing the thesis: domain knowledge + engineering craft + AI fluency + patient focus = valuable career.
