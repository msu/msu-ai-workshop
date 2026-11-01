<!-- Inline SVG, not an image file, so the text can use the deck fonts -->
<script setup lang="ts">
const chat = ['forgets your rules', 'you paste the slide', 'you copy the fix', 'can\'t build the PDF']
const agent = ['reads AGENTS.md', 'opens the deck file', 'fixes the typo in it', 'builds the PDF']
const session = [
  ['prompt', '> fix the typo on slide 4'],
  ['tool', '  Read 20_compilers.md'],
  ['tool', '  Edit 20_compilers.md'],
  ['del', '  - a compilier turns source'],
  ['add', '  + a compiler turns source'],
  ['tool', '  Done. One line changed.'],
]
</script>

<template>
  <svg class="chat-vs-agent" viewBox="0 0 480 448" role="img" aria-label="A browser chat window compared to a command line agent">
    <rect width="480" height="448" rx="8" class="backdrop" />

    <!-- browser -->
    <g transform="translate(16 16)">
      <rect width="290" height="200" rx="7" class="browser" />
      <path d="M0 30 V7 a7 7 0 0 1 7 -7 H283 a7 7 0 0 1 7 7 V30 Z" class="tab-strip" />
      <circle cx="13" cy="15" r="4" fill="#ff5f57" />
      <circle cx="26" cy="15" r="4" fill="#febc2e" />
      <circle cx="39" cy="15" r="4" fill="#28c840" />
      <path d="M54 30 V12 a6 6 0 0 1 6 -6 H150 a6 6 0 0 1 6 6 V30 Z" fill="#fff" />
      <text x="64" y="22" class="tab-title">AI Chat</text>
      <path d="M141 15 l6 6 m0 -6 l-6 6" class="icon" />

      <path d="M18 44 l-6 5 l6 5 M12 49 h13 M42 44 l6 5 l-6 5 M48 49 h-13" class="icon" />
      <rect x="60" y="38" width="220" height="22" rx="11" class="url-bar" />
      <rect x="70" y="47" width="8" height="7" rx="1" fill="#5f6368" />
      <path d="M71.5 47 v-2 a2.5 2.5 0 0 1 5 0 v2" class="icon" />
      <text x="84" y="53.5" class="url">chat.example.com</text>
      <line x1="0" x2="290" y1="66.5" y2="66.5" stroke="#dadce0" />

      <rect x="72" y="76" width="206" height="46" rx="10" class="user-bubble" />
      <text x="84" y="95" class="bubble-user">Fix the typo in this slide:</text>
      <text x="84" y="112" class="bubble-user">a compilier turns source</text>

      <rect x="12" y="132" width="206" height="56" rx="10" class="ai-bubble" />
      <text x="24" y="151" class="bubble-ai">Here is the fixed text:</text>
      <text x="24" y="168" class="bubble-ai">a compiler turns source</text>
      <rect x="228" y="164" width="50" height="22" rx="4" class="copy" />
      <text x="253" y="179" text-anchor="middle" class="copy-text">Copy</text>
    </g>
    <text x="322" y="50" class="heading">Chat Window</text>
    <g v-for="(point, i) in chat" :key="point">
      <circle cx="326" :cy="79 + i * 28" r="2.5" class="bullet" />
      <text x="336" :y="84 + i * 28" class="point">{{ point }}</text>
    </g>

    <!-- terminal -->
    <g transform="translate(16 232)">
      <rect width="290" height="200" rx="7" class="terminal" />
      <path d="M0 28 V7 a7 7 0 0 1 7 -7 H283 a7 7 0 0 1 7 7 V28 Z" class="title-bar" />
      <circle cx="13" cy="14" r="4" fill="#ff5f57" />
      <circle cx="26" cy="14" r="4" fill="#febc2e" />
      <circle cx="39" cy="14" r="4" fill="#28c840" />
      <text x="145" y="18.5" text-anchor="middle" class="title-text">my-course -- claude</text>
      <text v-for="([kind, line], i) in session" :key="line" x="12" :y="54 + i * 24" xml:space="preserve" :class="['term', kind]">{{ line }}</text>
    </g>
    <text x="322" y="266" class="heading">Coding Agent</text>
    <g v-for="(point, i) in agent" :key="point">
      <circle cx="326" :cy="295 + i * 28" r="2.5" class="bullet" />
      <text x="336" :y="300 + i * 28" class="point">{{ point }}</text>
    </g>
  </svg>
</template>

<style scoped>
.chat-vs-agent {
  width: 100%;
}

.backdrop {
  fill: #f3f4f6;
}

.browser {
  fill: #fff;
  stroke: #c9ccd1;
}

.tab-strip {
  fill: #dee1e6;
}

.tab-title {
  font-family: var(--sans);
  font-size: 12px;
  fill: #3c4043;
}

.icon {
  fill: none;
  stroke: #5f6368;
  stroke-width: 1.4;
}

.url-bar {
  fill: #f1f3f4;
}

.url {
  font-family: var(--sans);
  font-size: 12px;
  fill: #3c4043;
}

.user-bubble {
  fill: var(--msu-blue);
}

.ai-bubble {
  fill: #f1f3f4;
}

.bubble-user,
.bubble-ai {
  font-family: var(--sans);
  font-size: 13px;
}

.bubble-user {
  fill: #fff;
}

.bubble-ai {
  fill: #202124;
}

.copy {
  fill: #fff;
  stroke: #9aa0a6;
}

.copy-text {
  font-family: var(--sans);
  font-size: 12px;
  fill: #3c4043;
}

.terminal {
  fill: #1c1c1e;
}

.title-bar {
  fill: #3a3a3c;
}

.title-text {
  font-family: var(--sans);
  font-size: 12px;
  fill: #d1d1d6;
}

.term {
  font-family: var(--mono);
  font-size: 12.5px;
  fill: #c7c7cc;
  white-space: pre;
}

.term.prompt {
  fill: #fff;
}

.term.del {
  fill: #ff7b72;
}

.term.add {
  fill: #56d364;
}

.heading {
  font-family: var(--serif);
  font-size: 19px;
  font-weight: 600;
  fill: var(--msu-blue);
}

.point {
  font-family: var(--sans);
  font-size: 16px;
  fill: #1c2534;
}

.bullet {
  fill: var(--msu-gold);
}
</style>
