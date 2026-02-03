<template>
  <div class="comment-form">
    <h2>Add Comment</h2>
    <form @submit.prevent="submitComment">
      <input v-model="formData.name" type="text" placeholder="Your Name" required />
      <textarea v-model="formData.comment" placeholder="Your Comment" required></textarea>
      <button type="submit">Submit</button>
    </form>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const formData = ref({
  name: '',
  comment: ''
})

const submitComment = () => {
  console.log('Comment submitted:', formData.value)
  formData.value = { name: '', comment: '' }
}
</script>

<style scoped>
.comment-form {
  margin: 20px 0;
  padding: 20px;
  border: 1px solid #ddd;
  border-radius: 4px;
}

input, textarea {
  width: 100%;
  padding: 8px;
  margin: 10px 0;
  border: 1px solid #ccc;
  border-radius: 4px;
  font-family: Arial, sans-serif;
}

button {
  background-color: #007bff;
  color: white;
  padding: 10px 20px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #0056b3;
}
</style>
