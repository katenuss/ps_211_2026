<!--
  CltDemo: step-by-step Central Limit Theorem demo, driven by slide clicks.
  Usage (give the slide `clicks: 10` for n = 5, `clicks: 6` for larger n):
      <CltDemo :n="5" />
      <CltDemo :n="30" />
  Each click: draw a random sample of n songs, compute its mean, add the mean to a histogram.
  The random draws are seeded, so the demo is identical every time and works with the back key.

  Population: track_popularity (0-100) for 28,356 unique Spotify tracks.
  Spotify Web API via the spotifyr R package; compiled for TidyTuesday (2020-01-21).
  POP[v] = number of songs with popularity v. mu = 39.33, sigma = 23.70.
-->
<script setup>
import { computed } from 'vue'
import { useSlideContext } from '@slidev/client'

const props = defineProps({
  n: { type: Number, default: 5 },
  // Optional: force a stage instead of following the slide's clicks.
  stage: { type: Number, default: null },
})

const POP = [2620, 546, 360, 300, 231, 222, 187, 169, 189, 176, 160, 154, 146, 186, 185, 174, 198, 191, 220, 188, 198, 211, 194, 205, 228, 225, 260, 257, 257, 266, 336, 312, 338, 363, 370, 419, 418, 413, 452, 440, 460, 420, 406, 437, 441, 470, 409, 456, 441, 472, 474, 484, 464, 434, 474, 457, 446, 479, 430, 421, 443, 425, 399, 402, 362, 383, 349, 362, 320, 337, 297, 284, 242, 231, 236, 193, 201, 178, 134, 131, 85, 75, 57, 70, 42, 36, 29, 22, 28, 8, 16, 10, 5, 7, 5, 2, 1, 3, 5, 1, 1]
const TOTAL = POP.reduce((a, b) => a + b, 0)
const MU = POP.reduce((a, c, v) => a + c * v, 0) / TOTAL
const SIGMA = Math.sqrt(POP.reduce((a, c, v) => a + c * (v - MU) ** 2, 0) / TOTAL)
const REPS = 10000

// ---- seeded sampling (same draws every time) ------------------------------------------
function mulberry32(a) {
  return function () {
    a |= 0; a = (a + 0x6D2B79F5) | 0
    let t = Math.imul(a ^ (a >>> 15), 1 | a)
    t = (t + Math.imul(t ^ (t >>> 7), 61 | t)) ^ t
    return ((t ^ (t >>> 14)) >>> 0) / 4294967296
  }
}
const CUM = []
POP.reduce((a, c) => { CUM.push(a + c); return a + c }, 0)
function drawOne(rand) {
  const r = rand() * TOTAL
  let lo = 0, hi = 100
  while (lo < hi) { const mid = (lo + hi) >> 1; if (CUM[mid] > r) hi = mid; else lo = mid + 1 }
  return lo
}
const n = props.n
const rand = mulberry32(211 + n)
const SAMPLES = new Uint8Array(REPS * n)
const MEANS = new Float64Array(REPS)
for (let i = 0; i < REPS; i++) {
  let s = 0
  for (let j = 0; j < n; j++) { const v = drawOne(rand); SAMPLES[i * n + j] = v; s += v }
  MEANS[i] = s / n
}

// ---- what each click shows ---------------------------------------------------------------
// count = means in the histogram; show = index of the sample on display (-1 = none);
// mean = is its mean written out yet?
const detailed = n <= 8
const PLAN = detailed
  ? [
      { count: 0, show: -1, text: `Start with the <b>scores</b>. Song popularity is not normal: 9% of songs sit at 0.` },
      { count: 0, show: 0, mean: false, text: `<b>Step 1:</b> draw a random sample of ${n} songs.` },
      { count: 0, show: 0, mean: true, text: `<b>Step 2:</b> compute the sample mean.` },
      { count: 1, show: 0, mean: true, text: `<b>Step 3:</b> add that mean to a new histogram. Each block is the mean of one sample.` },
      { count: 1, show: 1, mean: true, text: `<b>Repeat:</b> a new sample of ${n} songs, a new mean.` },
      { count: 2, show: 1, mean: true, text: `Add it. Two samples, two different means.` },
      { count: 3, show: 2, mean: true, text: `A third sample, a third mean.` },
      { count: 10, show: 9, mean: true, text: `<b>10 samples.</b>` },
      { count: 100, show: 99, mean: true, text: `<b>100 samples.</b> A shape is starting to appear.` },
      { count: 1000, show: 999, mean: true, text: `<b>1,000 samples.</b>` },
      { count: 10000, show: 9999, mean: true, curve: true, text: `<b>10,000 samples:</b> a distribution of sample means. Centered on μ, narrower than the scores, and already close to the normal curve (dashed).` },
    ]
  : [
      { count: 0, show: -1, text: `Same songs, same recipe. This time each sample has <b>${n} songs</b>.` },
      { count: 0, show: 0, mean: true, text: `Draw ${n} random songs and compute their mean.` },
      { count: 1, show: 0, mean: true, text: `Add that mean to the histogram.` },
      { count: 10, show: 9, mean: true, text: `<b>10 samples.</b>` },
      { count: 100, show: 99, mean: true, text: `<b>100 samples.</b>` },
      { count: 1000, show: 999, mean: true, text: `<b>1,000 samples.</b>` },
      { count: 10000, show: 9999, mean: true, curve: true, text: `<b>10,000 samples:</b> the same bell shape (normal curve, dashed), packed much tighter around μ.` },
    ]

let clicksRef = null
try { clicksRef = useSlideContext().$clicks } catch (e) { clicksRef = null }
const step = computed(() => {
  const raw = props.stage ?? (clicksRef ? clicksRef.value : 0) ?? 0
  return PLAN[Math.max(0, Math.min(PLAN.length - 1, raw))]
})

// ---- geometry ------------------------------------------------------------------------------
const W = 900, H = 372
const X0 = 40, PX = 8.2                      // x(v) = X0 + v * PX, v in 0..100
const x = v => X0 + v * PX
const POP_BASE = 100, POP_H = 76             // scores panel
const MEAN_BASE = 336, MEAN_H = 98           // means panel
const INDIGO = '#6366f1', AMBER = '#f59e0b', RED = '#dc2626', DARK = '#312e81', GREY = '#d1d5db', INK = '#374151'

// scores: 25 bins of width 4 (the last one includes 100)
const POP_BW = 4
const popBars = (() => {
  const bins = new Array(25).fill(0)
  POP.forEach((c, v) => { bins[Math.min(24, Math.floor(v / POP_BW))] += c })
  const max = Math.max(...bins)
  return bins.map((c, i) => ({ x: x(i * POP_BW) + 1, w: POP_BW * PX - 2, h: (c / max) * POP_H }))
})()

// the sample on display
const sample = computed(() => {
  const i = step.value.show
  if (i < 0) return null
  const vals = Array.from(SAMPLES.slice(i * n, i * n + n))
  return { index: i, vals, mean: MEANS[i] }
})
// markers under the scores axis, stacked when values collide
const markers = computed(() => {
  if (!sample.value) return []
  const r = detailed ? 5 : 3.5
  const slot = detailed ? 1.4 : 1.0
  const used = {}
  return sample.value.vals.map(v => {
    const key = Math.round(v / slot)
    const k = used[key] = (used[key] ?? -1) + 1
    return { cx: x(v), cy: POP_BASE + 4 + r + k * (2 * r + 1), r }
  })
})
// value chips
const chips = computed(() => {
  if (!sample.value) return []
  const perRow = detailed ? n : Math.ceil(n / 2)
  const cw = detailed ? 46 : 30, ch = detailed ? 26 : 19, gap = detailed ? 8 : 4
  const left = detailed ? 182 : 168
  const top = detailed ? 150 : 143
  return sample.value.vals.map((v, j) => ({
    v, x: left + (j % perRow) * (cw + gap), y: top + Math.floor(j / perRow) * (ch + 4), w: cw, h: ch, fs: detailed ? 15 : 11.5,
  }))
})
const meanText = computed(() => {
  if (!sample.value || !step.value.mean) return ''
  const m = sample.value.mean.toFixed(1)
  return detailed ? `M = (${sample.value.vals.join(' + ')}) / ${n} = ${m}` : `M = (sum of the ${n} scores) / ${n} = ${m}`
})
const meanTextPos = computed(() => (detailed ? { x: 182, y: 201 } : { x: 168, y: 203 }))

// means histogram: 50 bins of width 2
const BW = 2, NB = 50
const binOf = m => Math.min(NB - 1, Math.floor(m / BW))
const hist = computed(() => {
  const count = step.value.count
  const bins = new Array(NB).fill(0)
  for (let i = 0; i < count; i++) bins[binOf(MEANS[i])]++
  const max = Math.max(1, ...bins)
  const unit = Math.min(13, MEAN_H / (max * 1.06))   // headroom for the normal curve
  const bw = BW * PX
  const newest = step.value.show >= 0 && step.value.show < count ? step.value.show : -1
  const shapes = []
  if (count <= 100) {
    // one block per mean, so single samples stay visible
    const fill = new Array(NB).fill(0)
    for (let i = 0; i < count; i++) {
      const b = binOf(MEANS[i]); const k = fill[b]++
      shapes.push({ x: x(b * BW) + 0.5, y: MEAN_BASE - (k + 1) * unit + 0.5, w: bw - 1, h: unit - 1, color: i === newest ? AMBER : INDIGO })
    }
  } else {
    bins.forEach((c, b) => { if (c) shapes.push({ x: x(b * BW) + 0.5, y: MEAN_BASE - c * unit, w: bw - 1, h: c * unit, color: INDIGO }) })
  }
  let curve = ''
  if (step.value.curve) {
    const se = SIGMA / Math.sqrt(n)
    const pts = []
    for (let v = 0; v <= 100; v += 0.25) {
      const pdf = Math.exp(-0.5 * ((v - MU) / se) ** 2) / (se * Math.sqrt(2 * Math.PI))
      pts.push(`${x(v).toFixed(1)},${(MEAN_BASE - count * BW * pdf * unit).toFixed(1)}`)
    }
    curve = 'M' + pts.join(' L')
  }
  return { shapes, curve, count }
})
const meansTitle = computed(() => {
  const c = hist.value.count
  if (c === 0) return 'Means: nothing here yet'
  return `Means: ${c.toLocaleString('en-US')} sample mean${c === 1 ? '' : 's'} (each from ${n} songs)`
})
const ticks = [0, 10, 20, 30, 40, 50, 60, 70, 80, 90, 100]
</script>

<template>
  <div class="clt-demo">
    <div class="clt-caption" v-html="step.text"></div>
    <svg :viewBox="`0 0 ${W} ${H}`" class="clt-svg" role="img" aria-label="Central Limit Theorem demo: samples of songs and a histogram of their means">
      <!-- scores -->
      <text :x="X0" y="14" class="t-title">Scores: popularity of 28,356 Spotify songs</text>
      <rect v-for="(b, i) in popBars" :key="'p' + i" :x="b.x" :y="POP_BASE - b.h" :width="b.w" :height="b.h" :fill="GREY" />
      <line :x1="X0" :x2="x(100)" :y1="POP_BASE" :y2="POP_BASE" stroke="#4b5563" stroke-width="1" />
      <line :x1="x(MU)" :x2="x(MU)" y1="20" :y2="POP_BASE" :stroke="DARK" stroke-width="2" stroke-dasharray="6 4" />
      <text :x="x(MU) + 6" y="30" class="t-mu">μ = {{ MU.toFixed(1) }}</text>
      <circle v-for="(m, i) in markers" :key="'m' + i" :cx="m.cx" :cy="m.cy" :r="m.r" :fill="AMBER" stroke="white" stroke-width="1" />

      <!-- the sample on display -->
      <template v-if="sample">
        <text :x="X0" :y="detailed ? 168 : 157" class="t-label">Sample {{ (sample.index + 1).toLocaleString('en-US') }}:</text>
        <g v-for="(c, i) in chips" :key="'c' + i">
          <rect :x="c.x" :y="c.y" :width="c.w" :height="c.h" rx="4" fill="#fef3c7" :stroke="AMBER" stroke-width="1" />
          <text :x="c.x + c.w / 2" :y="c.y + c.h / 2" :font-size="c.fs" class="t-chip">{{ c.v }}</text>
        </g>
        <text v-if="meanText" :x="meanTextPos.x" :y="meanTextPos.y" class="t-mean">{{ meanText }}</text>
      </template>

      <!-- means -->
      <text :x="X0" y="224" class="t-title">{{ meansTitle }}</text>
      <rect v-for="(s, i) in hist.shapes" :key="'h' + i" :x="s.x" :y="s.y" :width="s.w" :height="s.h" :fill="s.color" />
      <path v-if="hist.curve" :d="hist.curve" fill="none" :stroke="DARK" stroke-width="2" stroke-dasharray="5 4" />
      <line :x1="x(MU)" :x2="x(MU)" y1="232" :y2="MEAN_BASE" :stroke="DARK" stroke-width="2" stroke-dasharray="6 4" opacity="0.55" />
      <line :x1="X0" :x2="x(100)" :y1="MEAN_BASE" :y2="MEAN_BASE" stroke="#4b5563" stroke-width="1" />
      <g v-for="t in ticks" :key="'t' + t">
        <line :x1="x(t)" :x2="x(t)" :y1="MEAN_BASE" :y2="MEAN_BASE + 5" stroke="#4b5563" stroke-width="1" />
        <text :x="x(t)" :y="MEAN_BASE + 19" class="t-tick">{{ t }}</text>
        <line :x1="x(t)" :x2="x(t)" :y1="POP_BASE" :y2="POP_BASE + 4" stroke="#4b5563" stroke-width="1" />
      </g>
      <text :x="x(50)" :y="H - 2" class="t-axis">Popularity (0 to 100)</text>
    </svg>
  </div>
</template>

<style scoped>
.clt-demo { width: 100%; }
.clt-caption { font-size: 1.05rem; line-height: 1.35; min-height: 2.9rem; color: #111827; margin-bottom: 0.15rem; }
.clt-svg { display: block; width: 100%; max-width: 860px; margin: 0 auto; height: auto; }
.t-title { font-size: 14px; font-weight: 600; fill: #111827; }
.t-label { font-size: 15px; font-weight: 600; fill: #374151; }
.t-mu { font-size: 13px; fill: #312e81; }
.t-chip { text-anchor: middle; dominant-baseline: central; fill: #92400e; font-weight: 600; }
.t-mean { font-size: 16px; fill: #111827; font-weight: 600; }
.t-tick { font-size: 12px; fill: #4b5563; text-anchor: middle; }
.t-axis { font-size: 13px; fill: #374151; text-anchor: middle; }
</style>
