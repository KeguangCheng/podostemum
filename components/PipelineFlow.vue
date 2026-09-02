<script setup>
import { ref } from 'vue'

const STAGES = [
  {
    n: '1', title: 'Quality control', tone: 'slate',
    nodes: ['FastQC / MultiQC', 'TrimGalore', 'Rcorrector', 'Contamination screen'],
    detail: 'Every FASTQ through FastQC, aggregated with MultiQC for cross-library comparison. Adapters and bases below Q 30 removed; k-mer error correction, discarding reads that cannot be fixed. Contigs then screened for algal, fungal and bacterial contamination by taxonomic assignment of best hits and by GC-versus-coverage distribution.',
    risk: 'The root samples sit directly on the biofilm. Epiphytic algal transcripts assemble cleanly and annotate confidently as "plant", and non-stranded libraries give no strand signal to help separate them.',
  },
  {
    n: '2', title: 'De novo assembly', tone: 'teal',
    nodes: ['Trinity v2.x', 'CD-HIT-EST', 'BUSCO + ExN50', 'TransDecoder'],
    detail: 'All libraries pooled — root, leaf and mixed — into one de Bruijn graph assembly, giving a single coordinate system for every downstream comparison. Libraries are non-stranded, so no --SS_lib_type setting applies. CD-HIT-EST at 0.95-0.99 identity yields the Unigene set. Assembly quality read from BUSCO (embryophyta_odb10), ExN50 and read-representation rate together. TransDecoder predicts CDS and peptides.',
    risk: 'At ~40M PE reads per library the pooled assembly is memory-bound, so in-silico normalisation is effectively required. And elevated mutation rates in this family depress BUSCO for biological reasons, so it cannot be read alone.',
  },
  {
    n: '3', title: 'Annotation and orthology', tone: 'rose',
    nodes: ['BLASTX: NR / Swiss-Prot', 'Pfam domains', 'GO / KEGG', 'Proteinortho + gene trees'],
    detail: 'BLASTX at E ≤ 1e-5 against NR and Swiss-Prot, Pfam for domain architecture, TopGO and KOBAS for GO and KEGG enrichment. Orthologous groups inferred with Proteinortho against Arabidopsis thaliana, Populus trichocarpa and Cladopus chinensis.',
    risk: 'Under high divergence and deep paralogy, best-hit BLAST cannot separate WUS from WOX4 from WOX5 — and that separation is the experiment. Marker families get profile-HMM recall plus gene-tree placement instead.',
  },
  {
    n: '4', title: 'Quantification and readout', tone: 'violet',
    nodes: ['RSEM / Salmon', 'DESeq2', 'WGCNA', 'Identity atlas'],
    detail: 'Reads mapped back onto the Unigene reference for TPM. DESeq2 runs the single root-versus-leaf contrast at q < 0.05 and |log2FC| >= 1. The mixed samples are held out and fitted as a two-component mixture of root and leaf; genes the mixture cannot explain are candidates for transition-zone expression. WGCNA, the marker atlas and a tissue-specificity index complete the readout.',
    risk: 'DEG analysis answers "where is this gene higher". Fuzzy morphology predicts co-expression — a gene present in both root and leaf appears in no DEG list at all.',
  },
]

const active = ref(0)
</script>

<template>
  <div class="pf">
    <div class="pf-stages">
      <button
        v-for="(s, i) in STAGES" :key="s.n"
        class="pf-stage" :class="['t-' + s.tone, { on: active === i }]"
        @click="active = i; $event.currentTarget.blur()"
      >
        <span class="pf-n">{{ s.n }}</span>
        <span class="pf-t">{{ s.title }}</span>
        <span class="pf-nodes">{{ s.nodes.join(' · ') }}</span>
      </button>
    </div>

    <div class="pf-panel" :class="'p-' + STAGES[active].tone">
      <div class="pf-body">{{ STAGES[active].detail }}</div>
      <div class="pf-risk"><b>Key risk</b>{{ STAGES[active].risk }}</div>
    </div>

    <div class="pf-hint">Click a stage to see how it is done and what can go wrong</div>
  </div>
</template>

<style scoped>
.pf { font-size: 0.74rem; }

.pf-stages { display: grid; grid-template-columns: repeat(4, 1fr); gap: 0.5rem; }

.pf-stage {
  text-align: left; border: 1px solid #e2e8f0; background: #f8fafc;
  border-radius: 6px; padding: 0.5rem 0.65rem; cursor: pointer;
  transition: all 0.15s ease; border-top: 3px solid #cbd5e1;
}
.pf-stage:hover { background: #f1f5f9; }
.pf-stage.on { box-shadow: 0 2px 10px rgba(15, 23, 42, 0.10); }

.t-slate.on  { border-top-color: #475569; background: #f1f5f9; }
.t-teal.on   { border-top-color: #0d9488; background: #f0fdfa; }
.t-rose.on   { border-top-color: #be123c; background: #fff1f2; }
.t-violet.on { border-top-color: #6d28d9; background: #f5f3ff; }

.pf-n { color: #cbd5e1; font-weight: 700; font-size: 0.9rem; margin-right: 0.35rem; }
.pf-t { font-weight: 600; color: #1e293b; font-size: 0.8rem; }
.pf-nodes { display: block; color: #64748b; font-size: 0.62rem; line-height: 1.35; margin-top: 0.25rem; }

.pf-panel {
  margin-top: 0.75rem; border-radius: 6px; padding: 0.7rem 0.9rem;
  border: 1px solid #e2e8f0; border-left: 4px solid #cbd5e1; background: #f8fafc;
  min-height: 7.2rem;
}
.p-slate  { border-left-color: #475569; }
.p-teal   { border-left-color: #0d9488; background: #f0fdfa; }
.p-rose   { border-left-color: #be123c; background: #fff1f2; }
.p-violet { border-left-color: #6d28d9; background: #f5f3ff; }

.pf-body { color: #1e293b; line-height: 1.55; }
.pf-risk { margin-top: 0.5rem; color: #475569; font-size: 0.7rem; line-height: 1.5; }
.pf-risk b { color: #be123c; margin-right: 0.4rem; }

.pf-hint { margin-top: 0.5rem; color: #94a3b8; font-size: 0.64rem; text-align: right; }
</style>
