<script setup>
import { ref, onMounted } from 'vue'
import { createClient } from '@supabase/supabase-js'

// Replace with your Supabase URL and API key
const supabase = createClient('your-supabase-url', 'your-supabase-api-key')

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
