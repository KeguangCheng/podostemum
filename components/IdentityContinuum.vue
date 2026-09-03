<script setup>
import { ref, computed } from 'vue'

// 0 = base (attachment) -> 1 = distal (leaf tip)
const pos = ref(0.18)

const MODULES = [
  { key: 'wox5', label: 'WOX5 / SHR / SCR / PLT', role: 'root niche', color: '#15803d', bg: '#dcfce7' },
  { key: 'cle',  label: 'CLE41 / PXY / WOX4 / HB8', role: 'cambium',   color: '#0369a1', bg: '#e0f2fe' },
  { key: 'stm',  label: 'STM / WUS / CLV3',        role: 'shoot stem cells', color: '#b45309', bg: '#fef3c7' },
  { key: 'arp',  label: 'ARP (AS1) / YABBY / CUC', role: 'leaf determinacy',     color: '#be123c', bg: '#ffe4e6' },
]

const g = (x, mu, sd) => Math.exp(-((x - mu) ** 2) / (2 * sd * sd))

// Classical: narrow peaks, sharp boundaries, mutually exclusive
const classic = computed(() => {
  const x = pos.value
  return {
    wox5: g(x, 0.06, 0.085),
    cle:  g(x, 0.50, 0.10),
    stm:  g(x, 0.78, 0.055),
    arp:  g(x, 0.93, 0.085),
  }
})

// Fuzzy prediction: broad overlapping peaks, plus an ectopic basal STM/WUS shoulder
const fuzzy = computed(() => {
  const x = pos.value
  return {
    wox5: 0.85 * g(x, 0.10, 0.22),
    cle:  0.70 * g(x, 0.48, 0.26),
    stm:  Math.max(0.72 * g(x, 0.80, 0.24), 0.48 * g(x, 0.08, 0.16)),
    arp:  0.95 * g(x, 0.90, 0.30),
  }
})

const zone = computed(() => {
  const x = pos.value
  if (x < 0.34) return { name: 'R · Root · dissected, n = 3', color: '#15803d', sampled: true }
  if (x < 0.66) return { name: 'S · “Stem” · dissected, n = 3', color: '#7c3aed', sampled: true }
  return { name: 'L · Leaf · dissected, n = 3', color: '#b45309', sampled: true }
})

const pct = v => Math.round(Math.min(1, Math.max(0, v)) * 100)
</script>

<template>
  <div class="ic">
    <div class="ic-head">
      <span class="ic-hint">Drag the slider to move from the base of the plant to the distal tip</span>
      <span class="ic-zone" :style="{ color: zone.color, borderColor: zone.color }">{{ zone.name }}</span>
    </div>

    <input
      class="ic-slider" type="range" min="0" max="1" step="0.01"
      v-model.number="pos"
      @change="$event.target.blur()"
      @mouseup="$event.target.blur()"
    />

    <div class="ic-cover">
      <div class="ic-seg ic-seg-on"  style="flex:34">R · dissected</div>
      <div class="ic-seg ic-seg-on"  style="flex:32">S · “stem” · dissected</div>
      <div class="ic-seg ic-seg-on"  style="flex:34">L · dissected</div>
    </div>

    <div class="ic-axis">
      <span>Base · attached to rock</span>
      <span>Distal · photosynthetic leaf</span>
    </div>

    <div class="ic-cols">
      <div class="ic-col">
        <div class="ic-title">Classical CRS<span>modules mutually exclusive, sharp boundaries</span></div>
        <div v-for="m in MODULES" :key="'c' + m.key" class="ic-row">
          <div class="ic-lab">{{ m.label }}</div>
          <div class="ic-track" :style="{ background: m.bg }">
            <div class="ic-fill" :style="{ width: pct(classic[m.key]) + '%', background: m.color }"></div>
          </div>
        </div>
      </div>

      <div class="ic-col ic-col-hl">
        <div class="ic-title">Fuzzy-morphology prediction<span>modules overlap, graded co-expression</span></div>
        <div v-for="m in MODULES" :key="'f' + m.key" class="ic-row">
          <div class="ic-lab">{{ m.label }}<i>{{ m.role }}</i></div>
          <div class="ic-track" :style="{ background: m.bg }">
            <div class="ic-fill" :style="{ width: pct(fuzzy[m.key]) + '%', background: m.color }"></div>
          </div>
        </div>
      </div>
    </div>

    <div class="ic-foot">
      Schematic, not measured data. It states the two alternatives the TPM atlas has to tell apart. The middle of the axis, where the two models disagree most, is sampled in its own right, so the atlas can be read there directly rather than inferred.
    </div>
  </div>
</template>

<style scoped>
.ic { font-size: 0.72rem; }

.ic-head { display: flex; justify-content: space-between; align-items: center; margin-bottom: 0.3rem; }
.ic-hint { color: #94a3b8; font-size: 0.68rem; }
.ic-zone { font-weight: 600; font-size: 0.72rem; border: 1px solid; border-radius: 999px; padding: 0.05rem 0.6rem; }

.ic-slider { width: 100%; accent-color: #0d9488; height: 1.1rem; cursor: pointer; }

.ic-axis { display: flex; justify-content: space-between; color: #94a3b8; font-size: 0.64rem; margin-bottom: 0.7rem; }

.ic-cover { display: flex; gap: 2px; margin-top: 0.15rem; margin-bottom: 0.2rem; }
.ic-seg {
  font-size: 0.58rem; text-align: center; padding: 0.12rem 0.2rem;
  border-radius: 3px; line-height: 1.25; white-space: nowrap;
  overflow: hidden; text-overflow: ellipsis;
}
.ic-seg-on  { background: #ccfbf1; color: #0f766e; }
.ic-seg-off { background: #ffe4e6; color: #9f1239; }

.ic-cols { display: grid; grid-template-columns: 1fr 1fr; gap: 0.9rem; }

.ic-col { border: 1px solid #e2e8f0; border-radius: 6px; padding: 0.55rem 0.7rem; background: #f8fafc; }
.ic-col-hl { background: #f0fdfa; border-color: #99f6e4; }

.ic-title { font-weight: 600; color: #1e293b; font-size: 0.75rem; margin-bottom: 0.5rem; }
.ic-title span { display: block; font-weight: 400; color: #94a3b8; font-size: 0.62rem; }

.ic-row { margin-bottom: 0.4rem; }
.ic-lab { font-size: 0.62rem; color: #475569; display: flex; justify-content: space-between; }
.ic-lab i { font-style: normal; color: #94a3b8; }

.ic-track { height: 0.5rem; border-radius: 3px; overflow: hidden; margin-top: 0.1rem; }
.ic-fill { height: 100%; border-radius: 3px; transition: width 0.12s linear; }

.ic-foot { margin-top: 0.6rem; color: #94a3b8; font-size: 0.64rem; }
</style>
