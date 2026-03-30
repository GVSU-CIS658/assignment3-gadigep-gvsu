<template>
  <div class="syrup-layer" :style="syrupStyle"><slot /></div>
</template>

<script setup lang="ts">
import { computed } from 'vue'
const props = defineProps<{ syrup: string }>()

const colors: Record<string, string> = {
  'vanilla':  '#ffefd5',
  'caramel':  '#c68642',
  'hazelnut': '#7b3f00',
}
const syrupStyle = computed(() => {
  const c = colors[props.syrup]
  return {
    background: `repeating-linear-gradient(45deg, ${c}, ${c} 4px, transparent 4px, transparent 14px)`
  }
})
</script>