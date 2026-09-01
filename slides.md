---
theme: seriph
title: 'Organ Identity in Podostemum ceratophyllum'
info: |
  A comparative de novo transcriptomic strategy for testing "fuzzy morphology"
  in Podostemum ceratophyllum. Analysis plan.
lineNumbers: false
drawings:
  persist: false
transition: fade
mdc: true
aspectRatio: 16/9
layout: default
class: 'flex flex-col justify-center'
---

<div class="kicker">Analysis plan</div>

<div class="text-4xl font-semibold leading-tight" style="color:#0d9488">
Decoding Organ Identity in <i>Podostemum ceratophyllum</i>
</div>

<div class="text-lg text-slate-600 leading-snug pt-3" style="max-width:44rem">
A comparative de novo transcriptome strategy for testing “fuzzy morphology”
</div>

<div class="pt-6" style="max-width:40rem">
  <img src="./assets/fig-plant-insitu.jpg" class="rounded shadow-sm" />
  <div class="cred">Wood &amp; Freeman (2017) Fig. 1a–b<sup>3</sup> — leaves, stems and roots of <i>P. ceratophyllum</i> in a fast-flowing river</div>
</div>

<div class="pt-5">
<span class="tag tag-teal">Sequencing complete</span>
<span class="tag">Computational plan</span>
</div>

---

# What this deck covers

<div class="grid grid-cols-2 gap-8 pt-2">

<div>

### In scope

- **Why the question matters** — the morphological puzzle and the prior molecular evidence
- **What we are testing** — three falsifiable questions about organ identity
- **The pipeline** — QC → assembly → annotation → orthology → quantification → DEG → network
- **How we read the answer** — which pattern supports which conclusion
- **Limitations** — what this design can and cannot establish

</div>

<div>

### Where we start

<div class="card mb-2 fine">
<b>Data in hand.</b> Nine paired-end libraries — three partitions × three biological replicates. Sequencing is complete.
</div>

<div class="card mb-2 fine">
<b>No reference genome</b> for <i>P. ceratophyllum</i>. One genome exists for the entire family: <i>Cladopus chinensis</i>, published 2020<sup>20</sup>.
</div>

<div class="card mb-2 fine">
<b>Prior molecular evidence</b> is candidate-gene in situ hybridisation in three other podostemoid genera<sup>12,13</sup> — never transcriptome-wide, and never in this species.
</div>

<div class="card-teal fine">
The reference therefore has to be <b>built</b> before the question can be asked — which is what most of this deck is about.
</div>

</div>

</div>

---

# The organism

<div class="grid grid-cols-2 gap-7 pt-1">

<div>

<div class="kicker">A foundation species of eastern North American rivers<sup>3</sup></div>

- The **only** Podostemaceae species native to the continental U.S. and Canada — of roughly 135 in the Americas
- Dense monospecific stands in well-lit riffles; refuge and spawning habitat for benthic macroinvertebrates and fish
- Sequesters dissolved N, P, Ca and Zn; supplies organic carbon to the detrital food web
- Obligate rheophyte, clinging to bedrock through adhesive root hairs (*haptera*)

<div class="card-teal mt-3">
<b>Regionally imperilled.</b> Ohio: Endangered<sup>4</sup> · New York: Threatened, S2S3<sup>5</sup> · Maryland: S3<sup>6</sup> · Pennsylvania: S4. Survival tracks <b>local</b> habitat conditions — part of why baseline genomic resources carry conservation value.
</div>

</div>

<div class="pt-2">
  <img src="./assets/fig-ecosystem-role.png" class="rounded" />
  <div class="cred">Wood &amp; Freeman (2017) Fig. 2<sup>3</sup> — interaction with the benthic environment: elemental sink, carbon retention, sediment accumulation, substrate stabilisation</div>
</div>

</div>

---

# The classical model, and the misfits

<div class="grid grid-cols-2 gap-8 pt-4">

<div>

### Classical Root–Shoot model (CRS)

The vegetative body is built from **three discrete organ classes** with sharp boundaries and determinate homology.

<div class="flow mt-5 mb-4">
  <div class="node node-moss text-center"><b>Root</b></div>
  <div class="node node-sky text-center"><b>Stem</b></div>
  <div class="node node-amber text-center"><b>Leaf</b></div>
</div>

<div class="fine">
This framework underwrites essentially all comparative angiosperm morphology<sup>16</sup>.
</div>

</div>

<div>

### “Morphological misfits”

Podostemaceae and Lentibulariaceae deviate so far from CRS that conventional descriptive language **fails systematically**<sup>2</sup> — not at the margins, but at the level of naming the parts.

<div class="card-rose mt-5">
You cannot run a comparative analysis if you cannot first say which organ you are looking at.
</div>

<div class="fine mt-4">
This is exactly the situation in which a <b>molecular</b> criterion of identity becomes necessary rather than merely interesting<sup>1,7</sup>.
</div>

</div>

</div>

---

# What is actually derived in *P. ceratophyllum*

<div class="grid grid-cols-2 gap-7 pt-1">

<div>

<div class="card mb-3">
<b>Not the roots.</b> Crustose, thalloid and foliose roots are derived features of several <b>Old World</b> Podostemoideae genera — <i>Cladopus</i>, <i>Zeylanidium</i>, <i>Hydrobryum</i>. Rutishauser et al. found <i>P. ceratophyllum</i> comparatively <b>CRS-conformant</b><sup>10</sup>: filiform roots with a root cap, endogenous lateral roots, distinguishable stems and leaves.
</div>

<div class="card-teal mb-3">
<b>1 · Root-borne shoots.</b> Shoots arise endogenously <i>from the root</i>, not from a shoot apex, and Podostemoideae vegetative shoots generally lack a recognisable apical meristem with a permanent stem-cell pool<sup>10,12</sup>.
</div>

<div class="card-teal">
<b>2 · Dithecous leaves.</b> The leaf base bears two opposed stipule-like sheaths enclosing the next leaf or flower bud — producing a <b>non-axillary branching</b> pattern rare in angiosperms<sup>2,10</sup>.
</div>

</div>

<div class="pt-1">
  <img src="./assets/fig-stem-haptera.jpg" class="rounded" />
  <div class="cred">Wood &amp; Freeman (2017) Fig. 4<sup>3</sup> — stems bearing dense <i>haptera</i>, the adhesive root hairs that hold the plant to bedrock</div>

  <div class="card mt-3 text-center fine">
    A <b>mosaic</b>: relatively conventional roots, highly derived shoot and leaf construction. Anatomy alone cannot settle the histological homology of the parts.
  </div>
</div>

</div>

---

# Fuzzy morphology

<div class="lede">
Arber's partial-shoot theory of the leaf, extended by Sattler and Rutishauser<sup>8,9,16</sup>: category boundaries between “stem” and “leaf” are not absolute — organs occupy a developmental continuum and may express mixed or intermediate properties.
</div>

<IdentityContinuum />

---

# Phylogenetic frame and the loss of the SAM

<div class="grid grid-cols-2 gap-7 pt-1">

<div>

- Podostemaceae sit within **Malpighiales** (rosids), close to Hypericaceae / Clusiaceae<sup>11</sup>
- Three subfamilies — Tristichoideae, Weddellinoideae, **Podostemoideae**; the last is defined in part by the *spathella*, a non-vascular membrane enclosing the young flower<sup>2,11</sup>
- Tristichoideae retain a fairly typical SAM with sympodial-like branching<sup>12</sup>
- Podostemoideae, to which *P. ceratophyllum* belongs, are anatomically **SAM-less at every developmental stage** — all leaves arise repeatedly from a meristematic zone at the base of the preceding leaf<sup>12,13</sup>

<div class="card-teal mt-3">
The character is <b>polarised</b> along the phylogeny: whatever built the podostemoid body plan happened on the branch where the SAM was lost.
</div>

</div>

<div>
  <img src="./assets/fig-morph-phylo.png" class="rounded" style="max-height:17.5rem;margin:0 auto;display:block" />
  <div class="cred">Katayama, Koi &amp; Kato (2010) Fig. 1<sup>12</sup> — (A–C) SEM of shoots; (D–F) shoot development schemes; (G) subfamily phylogeny with the loss of the SAM marked</div>
</div>

</div>

---

# Saltational evolution and elevated mutation rates

<div class="grid grid-cols-5 gap-7 pt-1">

<div class="col-span-2">

Change severe enough to break the *Bauplan* — hence the “hopeful monsters” framing in the literature<sup>1,2</sup>.

<div class="card-rose mt-4">
Podostemaceae show <b>elevated nuclear substitution rates</b><sup>14</sup>, plastid genome restructuring and gene loss<sup>15</sup>. Deep rewiring, not gradual tuning.
</div>

<div class="card-amber mt-3">
<b>Analytical consequence.</b> Elevated substitution rates degrade sequence-similarity searches. This is not background colour — it directly shapes how I do orthology inference at stage 3 of the pipeline.
</div>

</div>

<div class="col-span-3 pt-3">
  <img src="./assets/fig-mutation-rate.png" class="rounded" />
  <div class="cred">Katayama et al. (2022) Fig. 3<sup>14</sup> — relative substitution rates over 1640 orthogroups. (a) Tristichoideae + Weddellinoideae against outgroups; (b) Podostemoideae against Tristichoideae + Weddellinoideae. Both distributions sit well above 1.</div>
</div>

</div>

---

# Prior molecular evidence — Katayama et al. (2010)

<div class="grid grid-cols-2 gap-7 pt-1">

<div>

<div class="card-teal mb-2">
<b>1 · Shoot–leaf identity fusion.</b> In normal angiosperms <i>STM</i> (indeterminate, shoot) and <i>ARP</i> (determinate, leaf) are <b>strictly mutually exclusive</b> in space. In SAM-less Podostemoideae the two are <b>co-expressed</b> in the young leaf/bract primordium, later resolving into a proximal <i>STM</i> domain and a distal <i>ARP</i> domain<sup>12</sup>.
</div>

<div class="card-teal mb-2">
<b>2 · Reversal of the compound-leaf logic.</b> Compound leaves normally arise by <i>adding</i> KNOX1 shoot character onto a leaf ground state. Here it is inverted: the shoot apex <b>loses</b> <i>STM</i>/<i>WUS</i> and <b>acquires</b> strong <i>ARP</i>, so an entire shoot is reduced to one terminal leaf<sup>12</sup>.
</div>

<div class="card-teal">
<b>3 · Root-borne shoot initiation.</b> <i>STM</i> and <i>WUS</i> are ectopically expressed near root tips, far from leaf tissue<sup>12,13</sup>.
</div>

<div class="fine mt-3">
Morphological novelty does not require a novel genome — decoupling and rewiring existing master regulators in space and time is sufficient.
</div>

</div>

<div class="pt-1">
  <img src="./assets/fig-organ-identity-model.png" class="rounded" />
  <div class="cred">Katayama, Koi &amp; Kato (2010) Fig. 7<sup>12</sup> — <i>STM</i> (yellow), <i>WUS</i> (blue), <i>ARP</i> (red). (C) the leaf/bract of Podostemoideae is genetically comparable to the whole shoot of other angiosperms; (D) shoot reduction across the subfamilies</div>
</div>

</div>

---

# Three core questions

<div class="space-y-3 pt-3">

<div class="card-teal">
<h3>Q1 · Homology</h3>
The three macroscopically separable partitions — <b>root / anchoring zone</b> (operationally <i>Thallus</i>), <b>putative vegetative stem</b>, and <b>dithecous leaf</b> — what underlying tissue homology do they show at whole-transcriptome scale?
</div>

<div class="card-sky">
<h3>Q2 · Boundary collapse</h3>
Do the four canonical cell-fate modules — <b>STM/WUS</b><sup>17</sup>, <b>ARP</b>, <b>WOX5/PLT</b><sup>18</sup>, <b>CLE41/WOX4</b><sup>19,25</sup> — show spatial cross-expression and regulatory boundary breakdown in this species?
</div>

<div class="card-amber">
<h3>Q3 · Coupling to stress</h3>
Under sustained hydrodynamic mechanical stress, is anomalous developmental-gene expression <b>co-ordinated with</b> secondary cell-wall, cell-polarity and abiotic-stress networks such as the NAC family<sup>26</sup>?
</div>

</div>

<div class="fine text-center mt-4">
Q1 and Q2 are testable with this dataset. Q3 is exploratory.
</div>

---

# The gap this fills

<div class="grid grid-cols-2 gap-7 pt-1">

<div>

<div class="kicker">Genomic resources for Podostemaceae are thin</div>

- Field access is restricted — the family survives only in pristine, fast-flowing water, and many species carry elevated extinction risk<sup>3</sup>
- Apart from the *Cladopus chinensis* genome<sup>20</sup>, the family has almost **no reference genome or transcriptome data**; *P. ceratophyllum* has none

<div class="card-teal mt-3">
<b>Why this project is feasible.</b> Material comes from a <b>cultivated NYBG population</b>: consistent developmental stage across replicates, fresh tissue, controlled dissection. It removes the field-access bottleneck that has held the family back.
</div>

<div class="card mt-2">
<b>Consequence for the design.</b> With no genome available we build the reference ourselves — deep RNA-seq plus <b>de novo assembly</b><sup>22,23,24</sup>.
</div>

</div>

<div class="pt-2">
  <img src="./assets/fig-cladopus.jpg" class="rounded" style="max-height:14.5rem;margin:0 auto" />
  <div class="cred">Xue et al. (2020) Fig. 1<sup>20</sup> — <i>Cladopus chinensis</i>, the only Podostemaceae species with a published genome: flowering plants in habitat, roots, leaves on sterile and fertile stems</div>
</div>

</div>

---

# Experimental design

<div class="grid grid-cols-5 gap-6">

<div class="col-span-3">

<div class="grid grid-cols-3 gap-3">
  <div class="card-moss">
    <h3>A · <i>Thallus</i></h3>
    <div class="fine">Root and substrate-anchoring partition.</div>
    <div class="finer mt-2">Operational name carried over from the original project naming — <b>not</b> a claim that this species has a true thalloid root.</div>
  </div>
  <div class="card-sky">
    <h3>B · Stem</h3>
    <div class="fine">The minute putative vegetative axis connecting anchoring tissue to the leaf cluster, with visible vascular traces.</div>
  </div>
  <div class="card-amber">
    <h3>C · Leaves</h3>
    <div class="fine">Distal laminar photosynthetic tissue bearing the dithecous sheath structure.</div>
  </div>
</div>

<div class="grid grid-cols-3 gap-3 mt-3 text-center fine">
  <div class="card"><b>3</b> partitions</div>
  <div class="card"><b>3</b> replicates each</div>
  <div class="card"><b>9</b> libraries</div>
</div>

<div class="card-amber mt-3">
<b>Statistical note.</b> n = 3 per group is the DESeq2 minimum. It is adequate for the large, consistent effects we expect from organ-identity genes, but underpowered for subtle or variable transcripts. I will report that constraint rather than work around it.
</div>

</div>

<div class="col-span-2 pt-1">
  <img src="./assets/fig-morph-variation.jpg" class="rounded" />
  <div class="cred">Wood &amp; Freeman (2017) Fig. 3<sup>3</sup> — morphological variation within <i>P. ceratophyllum</i>, all collected the same day in close proximity. Grid squares are 1 mm. The dissection has to be robust to this much plasticity.</div>
</div>

</div>

---

# The marker panel — four canonical modules

<div class="lede">Reference architecture in model eudicots; the yardstick every identity call is made against</div>

<table class="tbl">
<thead>
<tr>
<th style="width:17%">Organ system</th>
<th style="width:25%">Core modules and marker families</th>
<th>Developmental function in typical plants</th>
</tr>
</thead>
<tbody>
<tr>
<td><b>SAM</b><br/><span class="finer">undifferentiated stem-cell centre</span></td>
<td>Class I KNOX (<i>STM</i>, <i>KNAT1/2/6</i>) · WOX (<i>WUS</i>) · CLAVATA (<i>CLV3</i>)</td>
<td><i>STM</i> is expressed across the SAM, suppressing differentiation and maintaining stem-cell identity. <i>WUS</i> is confined to the organising centre and forms the classic negative-feedback loop with <i>CLV3</i> that sets stem-cell pool size and pluripotency.<sup>17</sup></td>
</tr>
<tr>
<td><b>Leaf primordium</b><br/><span class="finer">determinate differentiation</span></td>
<td>MYB-domain TFs (<i>ARP</i> / <i>AS1</i> / <i>AS2</i> / <i>PHAN</i>) · YABBY · CUC</td>
<td><i>AS1</i> switches on in peripheral primordium cells and directly represses <i>STM</i> and KNOX transcription, terminating indeterminate division and conferring determinacy plus adaxial–abaxial polarity.<sup>12</sup></td>
</tr>
<tr>
<td><b>RAM / QC</b><br/><span class="finer">root stem-cell niche</span></td>
<td><i>WOX5</i> · GRAS (<i>SHR</i>, <i>SCR</i>) · AP2 (<i>PLT1/2</i>)</td>
<td><i>WOX5</i> marks the quiescent centre and maintains niche autonomy; it is induced by the non-cell-autonomous <i>SHR</i>/<i>SCR</i> pair and converges with PLETHORA to fix the root developmental axis.<sup>18</sup></td>
</tr>
<tr>
<td><b>Vascular cambium</b><br/><span class="finer">radial thickening</span></td>
<td>CLE–PXY (<i>CLE41/44</i>, <i>PXY</i>/<i>TDR</i>) · <i>WOX4</i> · <i>HB8</i></td>
<td>Phloem-derived CLE41 peptide binds the PXY receptor kinase, activating <i>WOX4</i> and <i>HB8</i> and directing periclinal division and bidirectional xylem/phloem differentiation.<sup>19,25</sup></td>
</tr>
</tbody>
</table>

---

# Per-partition hypotheses and targets

<table class="tbl">
<thead>
<tr>
<th style="width:14%">Partition</th>
<th style="width:22%">Morphological hypothesis</th>
<th style="width:24%">Targeted marker set</th>
<th>Molecular test</th>
</tr>
</thead>
<tbody>
<tr>
<td><b>A · Thallus</b></td>
<td>Root partition combining anchorage, photosynthesis and ectopic shoot-forming potential</td>
<td>RAM markers: <i>WOX5</i>, <i>SHR</i>, <i>SCR</i>, PLT family<br/>Shoot initiation: <i>STM</i>, <i>WUS</i></td>
<td>Can a coherent root-cap and cortex regulatory network be recovered here? Is ectopic <i>STM</i>/<i>WUS</i> activation associated with shoot initiation in this partition?<sup>12</sup></td>
</tr>
<tr>
<td><b>B · Vegetative Stem</b></td>
<td>Central axis of secondary vascular development; transitional structure</td>
<td>Vascular polarity and stem cells: <i>CLE41/44</i>, <i>PXY</i>, <i>WOX4</i>, <i>HB8</i></td>
<td>Does the phloem–xylem axial differentiation module verify — i.e. does this partition retain the vascular-conductive “stem” identity signature?<sup>25</sup></td>
</tr>
<tr>
<td><b>C · Leaves</b></td>
<td>Dithecous photosynthetic organ of mixed shoot–leaf identity, apical dominance lost</td>
<td>Leaf determinacy and polarity: <i>ARP</i> (<i>AS1</i>), YABBY, CUC<br/>Apical stem cells: <i>STM</i>, <i>WUS</i>, <i>CLV3</i></td>
<td>In the SAM-less state, do the stem-cell maintenance network and the terminal leaf-differentiation network show graded co-expression and overlap?<sup>17</sup></td>
</tr>
</tbody>
</table>

<div class="card-teal mt-4 text-center">
Note the asymmetry: <b>A</b> and <b>C</b> test for <i>boundary collapse</i>; <b>B</b> tests for <i>boundary retention</i>. B is the internal control that keeps the whole design falsifiable.
</div>

---

# What each outcome would mean

<div class="lede">Committing to the interpretation before seeing the data</div>

<div class="space-y-3">

<div class="card grid grid-cols-12 gap-4 items-center">
<div class="col-span-5 fine"><b class="text-slate-800">Modules segregate cleanly by partition</b><br/>A = root markers, B = vascular, C = leaf markers, minimal overlap</div>
<div class="col-span-1 text-center arrow">→</div>
<div class="col-span-6 fine">CRS holds at the molecular level. Fuzzy morphology is <b>not</b> supported for this species — a genuine and publishable negative result.</div>
</div>

<div class="card-teal grid grid-cols-12 gap-4 items-center">
<div class="col-span-5 fine"><b class="text-slate-800">Graded co-expression of opposing modules</b><br/>e.g. KNOX1 and ARP both present in C; <i>STM</i>/<i>WUS</i> present in A</div>
<div class="col-span-1 text-center arrow">→</div>
<div class="col-span-6 fine">Molecular support for fuzzy morphology; identity is <b>continuous</b>, not categorical. This is what the prior literature predicts.</div>
</div>

<div class="card grid grid-cols-12 gap-4 items-center">
<div class="col-span-5 fine"><b class="text-slate-800">Modules absent or unrecoverable</b><br/>no confident orthologs assigned</div>
<div class="col-span-1 text-center arrow">→</div>
<div class="col-span-6 fine">Ambiguous — must separate true loss from <b>detection failure</b> under high sequence divergence. Handled explicitly at pipeline stage 3.</div>
</div>

<div class="card-amber grid grid-cols-12 gap-4 items-center">
<div class="col-span-5 fine"><b class="text-slate-800">All three partitions look alike</b><br/>few DEGs anywhere</div>
<div class="col-span-1 text-center arrow">→</div>
<div class="col-span-6 fine">Suspect a <b>technical</b> cause first — dissection carryover or insufficient depth — before reaching for a biological one.</div>
</div>

</div>

---

# The pipeline

<div class="lede">Four stages from raw reads to an identity call</div>

<PipelineFlow />

---

# Stage 1 · Quality control

<div class="grid grid-cols-2 gap-8 pt-2">

<div>

### Steps

1. **FastQC** on all 18 FASTQ files, aggregated with **MultiQC** for cross-library comparison
2. **TrimGalore** (or Trimmomatic) — remove sequencing adapters and low-quality bases below **Phred Q 30**
3. **Rcorrector** — k-mer error correction; discard reads unfixable through sequencing error or low complexity
4. Re-run FastQC to confirm the trim actually improved the libraries

<div class="fine mt-3">Following the published de novo workflows for non-model organisms<sup>22,23</sup>.</div>

</div>

<div>

### What I am checking for

- **Per-library consistency** — one bad replicate distorts every downstream contrast
- **Duplication rate** — high duplication with low complexity suggests over-amplification
- **rRNA carry-over** — poly(A) selection is imperfect in high-polysaccharide tissue
- **GC distribution** — a bimodal GC profile is the first hint of non-plant contamination

<div class="card-amber mt-4">
Assembly quality caps everything downstream, and de novo assembly has no reference to catch our mistakes for us.
</div>

</div>

</div>

---

# Stage 1b · The contamination problem

<div class="grid grid-cols-5 gap-7 pt-1">

<div class="col-span-3">

<div class="grid grid-cols-2 gap-5">

<div>

### Why this species is high-risk

- The plant is **submerged and epiphytised** — algal overgrowth is a documented decline driver<sup>3</sup>
- Partition A is the **substrate-attached** tissue, in direct contact with biofilm
- Cultivated NYBG material reduces but does not eliminate this
- A contaminating alga contributes real transcripts that assemble cleanly and annotate confidently as “plant”

</div>

<div>

### Mitigation

- Screen contigs by **taxonomic assignment of best hits** — flag those whose top hits are consistently algal, fungal or bacterial
- Cross-check **GC content against coverage** — contaminants usually form a distinct cloud
- Test whether flagged contigs are **partition-A-specific**
- Report the flagged set transparently rather than deleting it silently

</div>

</div>

<div class="card-rose mt-4">
<b>Open question:</b> filter contaminants before or after assembly? Pre-filtering is cleaner but risks discarding genuine low-coverage plant reads.
</div>

</div>

<div class="col-span-2 pt-1">
  <img src="./assets/fig-habitat.jpg" class="rounded" />
  <div class="cred">Katayama et al. (2022) Fig. 1<sup>14</sup> — podostemads in natural populations: plants on rocks in rapids, and riverbed rock covered by foliose roots. The tissue we sequence grows in a biofilm.</div>
</div>

</div>

---

# Stage 2 · De novo assembly with Trinity

<div class="grid grid-cols-2 gap-8 pt-2">

<div>

### Approach

No reference genome exists for *P. ceratophyllum*, so the transcript reference has to be built from the reads themselves.

**Trinity (v2.x)**<sup>24</sup> — de Bruijn graph assembly, run on **all nine libraries pooled**, so that a single common reference supports every cross-partition comparison.

<div class="card mt-4">
Minimum k-mer coverage threshold set permissively, so <b>low-abundance regulatory transcripts</b> are still reconstructed. Transcription factors are exactly the class we cannot afford to lose.
</div>

</div>

<div>

### Decisions to settle

<div class="card mb-3">
<b>Pooled vs per-partition assembly.</b> Pooling gives one coordinate system for quantification; per-partition assembly recovers partition-specific isoforms but complicates comparison. I favour <b>pooled</b>, with per-partition assemblies kept as a diagnostic check only.
</div>

<div class="card mb-3">
<b>In-silico read normalisation.</b> Cuts memory and runtime substantially, at some cost to rare transcripts. Worth testing both on one partition before committing.
</div>

<div class="card-amber">
<b>Strand-specificity.</b> Setting <code>--SS_lib_type</code> correctly materially improves the assembly, and it depends on the library chemistry used. <b>I need the kit and protocol details to get this right.</b>
</div>

</div>

</div>

---

# Stage 2b · Redundancy reduction and assembly QA

<div class="grid grid-cols-2 gap-8 pt-1">

<div>

### CD-HIT-EST → Unigenes

Trinity output is intentionally redundant — isoform splitting, allelic polymorphism, sequencing error. Uncorrected, this **splits read support** across duplicate contigs and deflates expression estimates.

<div class="card mt-3">
<b>Threshold trade-off.</b> 0.99 preserves close paralogs; 0.95 collapses more aggressively for a cleaner set, but risks merging recent duplicates that may have <i>diverged in function</i>. Given the paralogy risk I lean toward the conservative <b>0.99</b>, resolving duplicates later with gene trees.
</div>

<div class="card mt-3">
<b>Alternative worth discussing.</b> Corset or Trinity SuperTranscripts group transcripts by shared read support rather than sequence identity alone — better behaved for quantification, at the cost of a less familiar output format.
</div>

</div>

<div>

### Three quality measures, read together

<div class="grid grid-cols-1 gap-2">
  <div class="card fine"><b>BUSCO</b> against embryophyta_odb10 — complete, duplicated, fragmented, missing. High duplication would itself be informative.</div>
  <div class="card fine"><b>ExN50</b> — N50 restricted to the transcripts carrying the top <i>x</i>% of expression. More honest than raw N50, which long unsupported contigs inflate.</div>
  <div class="card fine"><b>Read representation</b> — the fraction of clean reads that map back. The most direct measure of what we have lost.</div>
</div>

<div class="card-teal mt-3">
<b>A caveat on BUSCO for this family.</b> Podostemaceae carry elevated mutation rates<sup>14</sup> and documented gene loss<sup>15</sup>, so a depressed score may reflect <b>real biology</b>. I plan to benchmark against the published <i>Cladopus chinensis</i> figures<sup>20</sup> rather than generic plant thresholds.
</div>

</div>

</div>

---

# Stage 3a · CDS prediction and functional annotation

<div class="grid grid-cols-2 gap-8 pt-2">

<div>

### CDS prediction

**TransDecoder** — identify likely coding regions and translate to peptide sequence.

<div class="card-teal mt-3">
Peptides, not nucleotides, are what we compare across deep divergence. Given elevated substitution rates in this family<sup>14</sup>, protein-level comparison is not a preference — it is the only level at which the signal survives.
</div>

</div>

<div>

### Functional annotation

- **BLASTX** at E-value **1e-5** against NCBI **NR** (broad homology) and **Swiss-Prot** (curated, high-confidence function)
- **Pfam** — protein domain architecture
- **GO** classification via **TopGO**; **KEGG** pathway enrichment via **KOBAS**<sup>21</sup>

<div class="card mt-4">
Domain architecture is more robust than raw similarity for our purpose: a divergent KNOX gene may fail a similarity threshold while still carrying an unmistakable homeodomain plus KNOX-A/B signature.
</div>

</div>

</div>

---

# Stage 3b · Orthology inference

<div class="lede">The step the whole argument depends on</div>

<div class="grid grid-cols-2 gap-8">

<div>

### Method

**Proteinortho** — combines sequence similarity with a graph-based reciprocal-best-hit criterion to infer orthologous groups across species.

<div class="kicker mt-4">Reference proteomes</div>

<div class="card mb-2 fine">
<b>Arabidopsis thaliana</b> — the module definitions live here; all four marker networks are characterised in this system
</div>

<div class="card mb-2 fine">
<b>Populus trichocarpa</b> — woody, well-annotated vascular cambium; the right reference for the CLE41/PXY/WOX4 module<sup>25</sup>
</div>

<div class="card-teal fine">
<b>Cladopus chinensis</b><sup>20</sup> — the only Podostemaceae genome; closest available relative and a direct control for family-level divergence
</div>

</div>

<div>

### Why single best-hit BLAST is insufficient

<div class="card-rose mb-3">
<b>1 · Elevated divergence.</b> Podostemaceae have anomalously high nuclear substitution rates<sup>14</sup>. A true <i>STM</i> ortholog may return a weak or misleading best hit.
</div>

<div class="card-rose mb-3">
<b>2 · Paralogy.</b> WOX, KNOX and NAC are large families, expanded in this lineage<sup>20</sup>, and best-hit assignment cannot reliably separate <i>WUS</i> from <i>WOX4</i> from <i>WOX5</i> — but that distinction <b>is</b> the experiment.
</div>

<div class="card-teal">
<b>Mitigation.</b> For the marker families specifically: build a profile HMM, retrieve all family members, align, and place candidates on a <b>gene tree</b> alongside characterised references. Assign identity by tree position, not by score rank.
</div>

</div>

</div>

---

# Stage 4a · Quantification and differential expression

<div class="grid grid-cols-2 gap-8 pt-2">

<div>

### RSEM / Salmon → the 9 × N matrix

Map each library's clean reads back onto the de novo Unigene reference; compute **TPM** (or FPKM) for unbiased expression estimates across all nine samples.

<div class="kicker mt-4">Quality gates before proceeding</div>

- **Mapping rate per library** — a low outlier flags a problem replicate
- **PCA and sample correlation heatmap** — replicates must cluster by partition, not by batch
- **Library size and normalisation factors**

<div class="card-rose mt-3">
<b>If replicates do not cluster by partition, I stop here.</b> Every downstream result would be built on an unreliable grouping, and the honest response is to revisit the dissection rather than press on.
</div>

</div>

<div>

### DESeq2 — three pairwise contrasts

<div class="grid grid-cols-3 gap-2 mb-3 text-center fine">
  <div class="card">Thallus <span class="text-slate-400">vs</span> Stem</div>
  <div class="card">Stem <span class="text-slate-400">vs</span> Leaves</div>
  <div class="card">Thallus <span class="text-slate-400">vs</span> Leaves</div>
</div>

<div class="fine mb-3">
Significance at Benjamini–Hochberg adjusted <i>q</i> &lt; 0.05 and |log2FoldChange| ≥ 1. Partition-specific up-regulated clusters then go to GO and KEGG enrichment by hypergeometric test.
</div>

<div class="card-amber">
<b>What DEG analysis cannot answer.</b> Pairwise DEGs answer <i>“where is this gene higher?”</i> — not <i>“what organ is this?”</i> Fuzzy morphology predicts <b>co-expression</b>: a gene present at comparable levels in all three partitions would be absent from every DEG list, yet is precisely the evidence for boundary collapse.
</div>

</div>

</div>

---

# Stage 4b · Network analysis and the identity readout

<div class="grid grid-cols-2 gap-8 pt-2">

<div>

### WGCNA co-expression modules

Cluster Unigenes into modules of co-varying expression, independent of any pairwise contrast — then correlate module eigengenes with partition identity, locate the marker genes **inside** the module structure, and pull out hub genes as candidate regulatory drivers.

<div class="card-teal mt-3">
If the SAM module and the leaf-determinacy module have <b>fused into a single co-expression module</b>, that is a far stronger statement about network topology than any list of individually significant genes.
</div>

<div class="card-amber mt-3">
<b>Caveat.</b> WGCNA is designed for many samples. With n = 9 the module structure will be coarse, and must be treated as exploratory rather than as a confirmed network.
</div>

</div>

<div>

### Three converging views

<div class="card-violet mb-2 fine">
<b>1 · Marker atlas.</b> Four canonical modules × three partitions, plotted in <b>absolute TPM</b> rather than fold change. This is the figure that answers Q2, and most likely the central figure of the paper.
</div>

<div class="card-violet mb-2 fine">
<b>2 · Specificity index.</b> A per-gene τ-type tissue-specificity index across the three partitions — turning “fuzzy vs discrete” from a verbal claim into a <b>distribution</b>.
</div>

<div class="card-violet mb-2 fine">
<b>3 · Cross-species comparison.</b> Correlate each partition's ortholog-restricted profile against published organ-specific transcriptomes<sup>21</sup>. Does the <i>Thallus</i> profile resemble a root, a stem, or neither?
</div>

<div class="card fine">
<b>No single view is decisive on its own.</b> Where the three disagree, that disagreement is itself a result worth reporting.
</div>

</div>

</div>

---

# Interpretation

<div class="grid grid-cols-2 gap-8 pt-1">

<div>

### Boundary dissolution as adaptation

To resist the shear forces of fast-flowing rivers, the plant must abandon vertical extension, a slender supporting taproot and a tall branched architecture.

<div class="space-y-1 mt-3">
  <div class="node node-rose"><b>Extreme hydrodynamic shear</b></div>
  <div class="text-center arrow">↓</div>
  <div class="node node-teal"><b>Loss of topological isolation between fate networks</b></div>
  <div class="text-center arrow">↓</div>
  <div class="node"><b>Compact planar body</b><span>anchorage, photosynthesis and stem-cell initiation co-located</span></div>
  <div class="text-center arrow">↓</div>
  <div class="node node-violet"><b>Fuzzy organ identity as observable outcome</b></div>
</div>

<div class="fine mt-3">
Heterochrony and heterotopy become the mechanism by which mechanical stability is purchased<sup>7,12</sup>.
</div>

</div>

<div>

### Stress–development cross-talk

<div class="card-amber mb-3">
<b>Flagged as a working hypothesis.</b> There is no direct experimental evidence for this in Podostemaceae. I present it as something the data can be interrogated for — not as a claim — and I will not pre-commit to specific gene identifiers.
</div>

<div class="fine mb-3">
NAC-family transcription factors act both in apical meristem development and CUC-mediated organ-boundary specification, and in mechanical-stress, drought and defence signalling<sup>26</sup>. Podostemaceae live permanently under mechanical stress, with alternating submergence and desiccation.
</div>

<div class="card-teal">
<b>What this dataset can do.</b> Test whether NAC-family and other stress-responsive TFs are differentially expressed between the putative stem and the putative root, and whether they fall into the <b>same co-expression modules</b> as the developmental markers. Module co-membership would be <i>suggestive of</i> coupling; it would not demonstrate causal recruitment.
</div>

</div>

</div>

---

# Limitations

<div class="grid grid-cols-2 gap-4 pt-2">

<div class="space-y-3">

<div class="card">
<b>Expression is not identity.</b> Transcript abundance is evidence about developmental programme, not proof of homology. The strongest available claim is <i>consistency with</i> a fuzzy-morphology model.
</div>

<div class="card-rose">
<b>No spatial resolution.</b> Bulk RNA-seq averages over every cell in a partition. Apparent co-expression of <i>STM</i> and <i>ARP</i> may reflect <b>two adjacent cell populations</b> rather than one mixed-identity cell. Distinguishing these needs in situ hybridisation<sup>12,13</sup> or single-cell methods — and the distinction is scientifically substantial.
</div>

<div class="card">
<b>No reference genome.</b> De novo assembly cannot fully separate paralogs, cannot report gene structure, and cannot establish whether a missing gene is truly absent or merely unassembled.
</div>

</div>

<div class="space-y-3">

<div class="card">
<b>n = 3.</b> Adequate for large, consistent differences; underpowered for subtle effects and for robust network inference.
</div>

<div class="card-rose">
<b>Partition boundaries are set by the hypothesis under test.</b> We separate partitions on morphological criteria, then ask whether those criteria correspond to molecular categories. Not circular — but partition assignment is an <b>assumption</b>, and carryover between adjacent partitions would bias toward the fuzzy result. This belongs in any write-up.
</div>

<div class="card">
<b>One species, one condition, one time point.</b> No developmental series, so heterochrony can be inferred but not observed.
</div>

</div>

</div>

---

# Summary

<div class="space-y-3 pt-3">

<div class="stage-row">
<div class="stage-num">1</div>
<div class="card fine">The morphological question is genuinely undecidable by anatomy alone. A molecular criterion of organ identity is the only route forward, and prior candidate-gene work in related genera<sup>12,13</sup> says the signal should be there.</div>
</div>

<div class="stage-row">
<div class="stage-num">2</div>
<div class="card fine">The design is falsifiable in both directions, and partition <b>B</b> is the internal control that keeps it so.</div>
</div>

<div class="stage-row">
<div class="stage-num">3</div>
<div class="card fine">The two places this project can quietly fail are <b>contamination</b> at assembly and <b>ortholog misassignment</b> under elevated divergence<sup>14</sup> and deep paralogy. Both have explicit mitigations built into the plan.</div>
</div>

<div class="stage-row">
<div class="stage-num">4</div>
<div class="card-teal fine">Pairwise DEG analysis alone would <b>systematically miss</b> the predicted signal, because the prediction is co-expression. The marker atlas, specificity index and co-expression modules are core analyses, not extras.</div>
</div>

<div class="stage-row">
<div class="stage-num">5</div>
<div class="card fine">At best this shows <b>consistency with</b> fuzzy morphology — plus a ranked candidate list and a first reference transcriptome for a regionally imperilled foundation species.</div>
</div>

</div>

---

# References — 1 to 13

<div class="reflist">

<div><span class="refn">1</span>Eckardt, N. A. &amp; Baum, D. (2010) The podostemad puzzle: the evolution of unusual morphology in the Podostemaceae [In Brief]. <i>The Plant Cell</i> <b>22</b>(7): 2104.</div>

<div><span class="refn">2</span>Rutishauser, R. (2016) Evolution of unusual morphologies in Lentibulariaceae (bladderworts and allies) and Podostemaceae (river-weeds): a pictorial report at the interface of developmental biology and morphological diversification. <i>Annals of Botany</i> <b>117</b>(5): 811–832.</div>

<div><span class="refn">3</span>Wood, J. &amp; Freeman, M. (2017) Ecology of the macrophyte <i>Podostemum ceratophyllum</i> Michx. (Hornleaf riverweed), a widespread foundation species of eastern North American rivers. <i>Aquatic Botany</i> <b>139</b>: 65–74.</div>

<div><span class="refn">4</span>Ohio Department of Natural Resources, Division of Natural Areas and Preserves (2024) <i>Rare Native Ohio Plants: 2024–25 Status List</i>. Columbus, OH.</div>

<div><span class="refn">5</span>New York Natural Heritage Program (2025) <i>Podostemum ceratophyllum</i> (riverweed) Species Status Assessment [draft]. Albany, NY.</div>

<div><span class="refn">6</span>Maryland Natural Heritage Program (2026) <i>List of Rare, Threatened, and Endangered Plants of Maryland, March 2026</i>. Maryland Department of Natural Resources, Annapolis, MD.</div>

<div><span class="refn">7</span>Minelli, A. (2022) Two-way exchanges between animal and plant biology, with focus on evo-devo. <i>Frontiers in Ecology and Evolution</i> <b>10</b>: 1057355.</div>

<div><span class="refn">8</span>Rutishauser, R. &amp; Isler, B. (2001) Developmental genetics and morphological evolution of flowering plants, especially bladderworts (<i>Utricularia</i>): fuzzy Arberian morphology complements classical morphology. <i>Annals of Botany</i> <b>88</b>(6): 1173–1202.</div>

<div><span class="refn">9</span>Rutishauser, R. (2020) EvoDevo: past and future of continuum and process plant morphology. <i>Philosophies</i> <b>5</b>(4): 41.</div>

<div><span class="refn">10</span>Rutishauser, R., Pfeifer, E., Moline, P. &amp; Philbrick, C. T. (2003) Developmental morphology of roots and shoots of <i>Podostemum ceratophyllum</i> (Podostemaceae – Podostemoideae). <i>Rhodora</i> <b>105</b>: 337–353.</div>

<div><span class="refn">11</span>Koi, S., Kita, Y., Hirayama, Y., Rutishauser, R., Huber, K. A. &amp; Kato, M. (2012) Molecular phylogenetic analysis of Podostemaceae: implications for taxonomy of major groups. <i>Botanical Journal of the Linnean Society</i> <b>169</b>(3): 461–492.</div>

<div><span class="refn">12</span>Katayama, N., Koi, S. &amp; Kato, M. (2010) Expression of <i>SHOOT MERISTEMLESS</i>, <i>WUSCHEL</i>, and <i>ASYMMETRIC LEAVES1</i> homologs in the shoots of Podostemaceae: implications for the evolution of novel shoot organogenesis. <i>The Plant Cell</i> <b>22</b>(7): 2131–2140.</div>

<div><span class="refn">13</span>Koi, S. &amp; Katayama, N. (2013) Gene expression analysis of aquatic angiosperms Podostemaceae to gain insight into the evolution of their enigmatic morphology. In: De Smet, I. (ed.) <i>Plant Organogenesis</i>. Methods in Molecular Biology, vol. 959, pp. 83–95. Humana Press, Totowa, NJ.</div>

</div>

---

# References — 14 to 26

<div class="reflist">

<div><span class="refn">14</span>Katayama, N., Koi, S., Sassa, A., Kurata, T., Imaichi, R., Kato, M. &amp; Nishiyama, T. (2022) Elevated mutation rates underlie the evolution of the aquatic plant family Podostemaceae. <i>Communications Biology</i> <b>5</b>: 75.</div>

<div><span class="refn">15</span>Bedoya, A. M., Ruhfel, B. R., Philbrick, C. T., Madriñán, S., Bove, C. P., Mesterházy, A. &amp; Olmstead, R. G. (2019) Plastid genomes of five species of riverweeds (Podostemaceae): structural organization and comparative analysis in Malpighiales. <i>Frontiers in Plant Science</i> <b>10</b>: 1035.</div>

<div><span class="refn">16</span>Sattler, R. (2026) Articulation morphology of plants and plant evo-devo: an open morphology—empirical, dynamic, all-inclusive, and unifying. <i>Plants</i> <b>15</b>(5): 730.</div>

<div><span class="refn">17</span>Kean-Galeno, T., Lopez-Arredondo, D. &amp; Herrera-Estrella, L. (2024) The shoot apical meristem: an evolutionary molding of higher plants. <i>International Journal of Molecular Sciences</i> <b>25</b>(3): 1519.</div>

<div><span class="refn">18</span>Pardal, R. &amp; Heidstra, R. (2021) Root stem cell niche networks: it's complexed! Insights from <i>Arabidopsis</i>. <i>Journal of Experimental Botany</i> <b>72</b>(19): 6727–6738.</div>

<div><span class="refn">19</span>Etchells, J. P. &amp; Turner, S. R. (2010) Orientation of vascular cell divisions in <i>Arabidopsis</i>. <i>Plant Signaling &amp; Behavior</i> <b>5</b>(6): 730–732.</div>

<div><span class="refn">20</span>Xue, T., Zheng, X., Chen, D. et al. (2020) A high-quality genome provides insights into the new taxonomic status and genomic characteristics of <i>Cladopus chinensis</i> (Podostemaceae). <i>Horticulture Research</i> <b>7</b>: 46.</div>

<div><span class="refn">21</span>Gao, H., Zhao, Y., Huang, L., Huang, Y., Chen, J., Zhou, H. &amp; Zhang, X. (2022) Comparative analysis of buds transcriptome and identification of two florigen gene AkFTs in <i>Amorphophallus konjac</i>. <i>Scientific Reports</i> <b>12</b>: 6782.</div>

<div><span class="refn">22</span>Jackson, D. J., Cerveau, N. &amp; Posnien, N. (2024) De novo assembly of transcriptomes and differential gene expression analysis using short-read data from emerging model organisms – a brief guide. <i>Frontiers in Zoology</i> <b>21</b>: 17.</div>

<div><span class="refn">23</span>Raghavan, V., Kraft, L., Mesny, F. &amp; Rigerte, L. (2022) A simple guide to de novo transcriptome assembly and annotation. <i>Briefings in Bioinformatics</i> <b>23</b>(2): bbab563.</div>

<div><span class="refn">24</span>Grabherr, M. G. et al. (2011) Full-length transcriptome assembly from RNA-Seq data without a reference genome. <i>Nature Biotechnology</i> <b>29</b>: 644–652.</div>

<div><span class="refn">25</span>Galibina, N. A., Moshchenskaya, Y. L., Tarelkina, T. V. et al. (2023) Identification and expression profile of CLE41/44-PXY-WOX genes in adult trees <i>Pinus sylvestris</i> L. trunk tissues during cambial activity. <i>Plants</i> <b>12</b>(4): 835.</div>

<div><span class="refn">26</span>Nuruzzaman, M., Sharoni, A. M. &amp; Kikuchi, S. (2013) Roles of NAC transcription factors in the regulation of biotic and abiotic stress responses in plants. <i>Frontiers in Microbiology</i> <b>4</b>: 248.</div>

</div>

<div class="finer mt-3" style="color:#94a3b8">
Figures on slides 1, 3, 5, 7, 8, 9, 11, 12 and 18 are reproduced from refs 3, 12, 14 and 20 for internal academic discussion; each is credited on the slide where it appears.
</div>
