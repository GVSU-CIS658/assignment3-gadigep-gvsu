<template>
  <div class="app">
    <h1>Custom Drink Maker</h1>
    <div class="controls">
      <fieldset>
        <legend>Base Beverage</legend>
        <label v-for="b in bases" :key="b.value">
          <input type="radio" name="base" :value="b.value" v-model="selectedBase" />
          {{ b.label }}
        </label>
      </fieldset>

      <fieldset>
        <legend>Creamer</legend>
        <label v-for="c in creamers" :key="c.value">
          <input type="radio" name="creamer" :value="c.value" v-model="selectedCreamer" />
          {{ c.label }}
        </label>
      </fieldset>

      <fieldset>
        <legend>Syrup</legend>
        <label v-for="s in syrups" :key="s.value">
          <input type="radio" name="syrup" :value="s.value" v-model="selectedSyrup" />
          {{ s.label }}
        </label>
      </fieldset>
    </div>

    <Beverage
      :base="selectedBase"
      :creamer="selectedCreamer"
      :syrup="selectedSyrup"
    />
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import Beverage from './components/Beverage.vue'

const bases = [
  { value: 'coffee',    label: 'Coffee' },
  { value: 'green-tea', label: 'Green Tea' },
  { value: 'black-tea', label: 'Black Tea' },
]

const creamers = [
  { value: 'none',        label: 'No Creamer' },
  { value: 'milk',        label: 'Milk' },
  { value: 'cream',       label: 'Cream' },
  { value: 'half-half',   label: 'Half & Half' },
]

const syrups = [
  { value: 'none',     label: 'No Syrup' },
  { value: 'vanilla',  label: 'Vanilla' },
  { value: 'caramel',  label: 'Caramel' },
  { value: 'hazelnut', label: 'Hazelnut' },
]

const selectedBase    = ref('coffee')
const selectedCreamer = ref('none')
const selectedSyrup   = ref('none')
</script>

<style scoped>
.app {
  display: grid;
  gap: 1.25rem;
  justify-items: center;
}

h1 {
  font-size: 2rem;
  margin: 0;
}

.controls {
  display: grid;
  grid-template-columns: repeat(3, minmax(180px, 1fr));
  gap: 0.75rem;
  width: min(900px, 100%);
}

fieldset {
  border: 1px solid #d0d0d0;
  border-radius: 8px;
  padding: 0.7rem 0.8rem;
  text-align: left;
  background: rgba(255, 255, 255, 0.8);
}

legend {
  font-weight: 600;
  padding: 0 0.3rem;
}

label {
  display: block;
  margin: 0.3rem 0;
  cursor: pointer;
}

input {
  margin-right: 0.45rem;
}

@media (max-width: 820px) {
  .controls {
    grid-template-columns: 1fr;
  }
}
</style>