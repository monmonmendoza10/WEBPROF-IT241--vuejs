<script setup>
import { ref, onMounted } from 'vue'
import { supabase } from './lib/supabaseClient'

const instruments = ref([])

async function getInstruments() {
  try {
    const { data, error } = await supabase.from('instruments').select()
    
    if (error) throw error

    instruments.value = data
  } catch (err) {
    console.error('Error fetching instruments:', err)
  }
}

onMounted(() => {
  getInstruments()
})
</script>

<template>
  <div>
    <h1>Instrument List</h1>
    <ul>
      <li v-for="instrument in instruments" :key="instrument.id">
        {{ instrument.name }}
      </li>
    </ul>
  </div>
</template>

<style scoped>
/* Add your custom styles here */
</style>
