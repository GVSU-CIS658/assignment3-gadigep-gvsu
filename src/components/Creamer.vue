<template>
  <div class="creamer-layer" :class="{ 'no-syrup': !hasSyrup }" :style="creamStyle"></div>
</template>

<script setup lang="ts">
import { computed } from 'vue'
const props = defineProps<{ creamer: string; hasSyrup: boolean }>()

const colors: Record<string, string> = {
  'milk':      'rgba(240,240,230,0.85)',
  'cream':     'rgba(255,253,245,0.92)',
  'half-half': 'rgba(245,230,200,0.88)',
}
const creamStyle = computed(() => ({ background: colors[props.creamer] ?? 'transparent' }))
</script>

<style scoped>
.creamer-layer {
  position: absolute;
  left: 0;
  right: 0;
  bottom: 70%;
  height: 15%;
  transition: background 220ms ease;
}

.creamer-layer.no-syrup {
  bottom: 55%;
}
</style>