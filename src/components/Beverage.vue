<template>
  <div class="mug">
    <div class="mug-body">
      <Base :base="base">
        <!-- Only show syrup if a syrup is chosen -->
        <Syrup v-if="syrup !== 'none'" :syrup="syrup">
          <!-- Creamer sits on top of syrup, or directly on base if no syrup -->
          <Creamer v-if="creamer !== 'none'" :creamer="creamer" />
        </Syrup>

        <!-- If no syrup but creamer chosen: creamer directly on base (no gap) -->
        <Creamer
          v-if="creamer !== 'none' && syrup === 'none'"
          :creamer="creamer"
        />
      </Base>
    </div>
    <div class="mug-handle"></div>
  </div>
</template>

<script setup lang="ts">
import Base from './Base.vue'
import Creamer from './Creamer.vue'
import Syrup from './Syrup.vue'

defineProps<{
  base: string
  creamer: string
  syrup: string
}>()
</script>