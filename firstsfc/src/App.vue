<script setup>
import { ref, onMounted } from 'vue'
import { supabase } from './lib/supabaseClient'

const instruments = ref([])
const loading = ref(true)
const error = ref(null)

async function getInstruments() {
  try {
    loading.value = true
    const { data, error: err } = await supabase.from('instruments').select()
    if (err) throw err
    instruments.value = data || []
  } catch (err) {
    error.value = err.message
    console.error('Error fetching instruments:', err)
  } finally {
    loading.value = false
  }
}

onMounted(() => {
   getInstruments()
})
</script>

<template>
  <div class="container">
    <h1>Musical Instruments</h1>
    
    <div v-if="loading" class="loading">Loading instruments...</div>
    <div v-else-if="error" class="error">{{ error }}</div>
    <div v-else-if="instruments.length === 0" class="empty">No instruments found</div>
    <div v-else>
      <ul class="instruments-list">
        <li v-for="instrument in instruments" :key="instrument.id" class="instrument-item">
          {{ instrument.name }}
        </li>
      </ul>
    </div>
  </div>
</template>

<style scoped>
.container {
  max-width: 600px;
  margin: 40px auto;
  padding: 20px;
  font-family: Arial, sans-serif;
}

h1 {
  color: #333;
  text-align: center;
  margin-bottom: 30px;
}

.instruments-list {
  list-style: none;
  padding: 0;
}

.instrument-item {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  padding: 15px 20px;
  margin: 10px 0;
  border-radius: 8px;
  font-size: 18px;
  font-weight: 500;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  transition: transform 0.2s;
}

.instrument-item:hover {
  transform: translateY(-2px);
  box-shadow: 0 6px 12px rgba(0, 0, 0, 0.15);
}

.loading, .error, .empty {
  text-align: center;
  padding: 20px;
  font-size: 16px;
}

.error {
  color: #d32f2f;
  background: #ffebee;
  padding: 20px;
  border-radius: 8px;
}

.empty {
  color: #666;
}
</style>