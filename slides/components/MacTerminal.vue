<!-- Inline SVG of a dark macOS Terminal window on a white panel.
     A loop types a cd and an ls. With the still prop, it shows only the final frame -->
<script setup lang="ts">
import { computed, onMounted, onUnmounted, ref, useId } from 'vue'

const props = defineProps({
  still: { type: Boolean, default: false },
})

// Each instance needs its own SVG ids. A shared id resolves to the first copy, and a hidden slide can hold that copy.
const uid = useId()

const CHAR_WIDTH = 8.4
const HOME = 'faculty@macbook ~ % '
const COURSE = 'faculty@macbook my-course % '
const LOGIN = ['muted', 'Last login: Wed Nov  4 11:58:02 on ttys000']
const LISTING = [
  ['', 'AGENTS.md    lectures/'],
  ['', 'quizzes/     syllabus.md'],
  ['', COURSE],
]
const FINAL = [
  LOGIN,
  ['', `${HOME}cd courses/my-course`],
  ['', `${COURSE}ls`],
  ...LISTING,
]

const lines = ref(props.still ? FINAL : [LOGIN, ['', HOME]])
const typing = ref(false)
let running = true

const cursorX = computed(() => 12 + lines.value[lines.value.length - 1][1].length * CHAR_WIDTH)
const cursorY = computed(() => 40 + (lines.value.length - 1) * 21)

function wait(ms: number) {
  return new Promise(resolve => setTimeout(resolve, ms))
}

async function type(command: string) {
  typing.value = true
  for (const char of command) {
    if (!running) return
    const last = lines.value.length - 1
    lines.value[last] = ['', lines.value[last][1] + char]
    await wait(90)
  }
  typing.value = false
}

async function play() {
  while (running) {
    lines.value = [LOGIN, ['', HOME]]
    await wait(1400)
    await type('cd courses/my-course')
    await wait(500)
    lines.value.push(['', COURSE])
    await wait(1200)
    await type('ls')
    await wait(500)
    lines.value.push(...LISTING)
    await wait(6000)
  }
}

onMounted(() => {
  if (!props.still) play()
})
onUnmounted(() => { running = false })
</script>

<template>
  <svg class="mac-terminal" viewBox="0 0 480 340" role="img" aria-label="A macOS Terminal window where a user changes directory and lists the files">
    <defs>
      <linearGradient :id="`${uid}-bar`" x1="0" x2="0" y1="0" y2="1">
        <stop offset="0" stop-color="#4a4a4c" />
        <stop offset="1" stop-color="#363638" />
      </linearGradient>
      <filter :id="`${uid}-shadow`" x="-15%" y="-15%" width="130%" height="140%">
        <feDropShadow dx="0" dy="10" stdDeviation="12" flood-color="#000" flood-opacity="0.35" />
      </filter>
    </defs>

    <rect width="480" height="340" rx="8" fill="#fff" />

    <g transform="translate(28 34)">
      <rect width="424" height="266" rx="10" fill="#1e1e1e" :filter="`url(#${uid}-shadow)`" />
      <path d="M0 28 V10 a10 10 0 0 1 10 -10 H414 a10 10 0 0 1 10 10 V28 Z" :fill="`url(#${uid}-bar)`" />
      <line x1="0" x2="424" y1="28.5" y2="28.5" stroke="#000" />

      <circle cx="16" cy="14" r="6" fill="#ff5f57" stroke="#e0443e" stroke-width="0.5" />
      <circle cx="36" cy="14" r="6" fill="#febc2e" stroke="#dea123" stroke-width="0.5" />
      <circle cx="56" cy="14" r="6" fill="#28c840" stroke="#1aab29" stroke-width="0.5" />
      <text x="212" y="18.5" text-anchor="middle" class="title">my-course -- zsh -- 80x24</text>

      <text v-for="([kind, line], i) in lines" :key="i" x="12" :y="54 + i * 21" xml:space="preserve" :class="['line', kind]">{{ line }}</text>
      <rect :x="cursorX" :y="cursorY" width="9" height="17" :class="['cursor', { blink: !typing }]" />
    </g>
  </svg>
</template>

<style scoped>
.mac-terminal {
  width: 100%;
}

.title {
  font-family: -apple-system, "SF Pro Text", var(--sans);
  font-size: 12.5px;
  font-weight: 500;
  fill: #c8c8ca;
}

.line {
  font-family: "SF Mono", Menlo, var(--mono);
  font-size: 14px;
  fill: #f2f2f2;
  white-space: pre;
}

.line.muted {
  fill: #a0a0a2;
}

.cursor {
  fill: #d0d0d0;
}

.cursor.blink {
  animation: blink 1s steps(1) infinite;
}

@keyframes blink {
  50% { opacity: 0; }
}
</style>
