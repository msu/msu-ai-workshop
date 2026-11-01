<!-- A real interactive figure, from slides/public/figures, that I can click during the talk -->
<script setup lang="ts">
const props = defineProps<{ file: string, title: string }>()
const src = `${import.meta.env.BASE_URL}figures/${props.file}`
</script>

<template>
  <iframe class="live-figure" :src="src" :title="title" />
</template>

<style scoped>
.live-figure {
  width: 100%;
  height: 300px;
  border: 0;
  border-radius: 10px;
  background: #f4f4f4;
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.45);
}
</style>
