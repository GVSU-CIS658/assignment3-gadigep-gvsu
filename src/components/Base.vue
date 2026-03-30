<template>
  <div class="base-layer" :style="baseStyle"><slot /></div>
</template>

<script setup lang="ts">
import { computed } from 'vue'
const props = defineProps<{ base: string }>()

const configs: Record<string, string> = {
  'coffee':    'linear-gradient(180deg,#6b3a1f,#4a2c0a)',
  'green-tea': 'linear-gradient(180deg,#a8c97a,#5a7d3a)',
  'black-tea': 'linear-gradient(180deg,#d4874a,#8b4513)',
}
const baseStyle = computed(() => ({ background: configs[props.base] ?? configs['coffee'] }))
</script>