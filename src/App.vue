<template>
  <div class="app">
    <h1>☕ Custom Drink Maker</h1>
    <div class="controls">
      <!-- Base Beverage -->
      <fieldset>
        <legend>Base Beverage</legend>
        <label v-for="b in bases" :key="b.value">
          <input type="radio" name="base" :value="b.value" v-model="selectedBase" />
          {{ b.label }}
        </label>
      </fieldset>

      <!-- Creamer -->
      <fieldset>
        <legend>Creamer</legend>
        <label v-for="c in creamers" :key="c.value">
          <input type="radio" name="creamer" :value="c.value" v-model="selectedCreamer" />
          {{ c.label }}
        </label>
      </fieldset>

      <!-- Syrup -->
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