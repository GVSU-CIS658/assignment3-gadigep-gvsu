<template>
  <div class="creamer-layer" :style="creamStyle"><slot /></div>
</template>

<script setup lang="ts">
import { computed } from 'vue'
const props = defineProps<{ creamer: string }>()

const colors: Record<string, string> = {
  'milk':      'rgba(240,240,230,0.85)',
  'cream':     'rgba(255,253,245,0.92)',
  'half-half': 'rgba(245,230,200,0.88)',
}
const creamStyle = computed(() => ({ background: colors[props.creamer] ?? 'transparent' }))
</script>