<template>
  <Mug>
    <Contents>
      <template #bottom>
        <Base :base="base" />
      </template>

      <template v-if="showSyrup" #mid>
        <Syrup :syrup="syrup" />
      </template>

      <template v-if="showCreamer" #top>
        <Creamer :creamer="creamer" :has-syrup="showSyrup" />
      </template>
    </Contents>
  </Mug>
</template>

<script setup lang="ts">
import { computed } from 'vue'
import Mug from './Mug.vue'
import Contents from './Contents.vue'
import Base from './Base.vue'
import Creamer from './Creamer.vue'
import Syrup from './Syrup.vue'

const props = defineProps<{
  base: string
  creamer: string
  syrup: string
}>()

const showSyrup = computed(() => props.syrup !== 'none')
const showCreamer = computed(() => props.creamer !== 'none')
</script>