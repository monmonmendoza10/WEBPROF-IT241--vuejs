<template>
  <div class="comment">
    <h3>Comments</h3>
    <div v-if="comments.length === 0" class="no-comments">
      No comments yet.
    </div>
    <div v-else class="comments-list">
      <div v-for="(comment, index) in comments" :key="index" class="comment-item">
        <p><strong>{{ comment.name }}</strong></p>
        <p>{{ comment.comment }}</p>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const comments = ref([])
</script>

<style scoped>
.comment {
  margin: 20px 0;
  padding: 20px;
  border: 1px solid #eee;
  border-radius: 4px;
}

.no-comments {
  color: #999;
  font-style: italic;
}

.comments-list {
  display: flex;
  flex-direction: column;
  gap: 15px;
}

.comment-item {
  padding: 10px;
  border-left: 4px solid #007bff;
  background-color: #f9f9f9;
}

.comment-item p {
  margin: 5px 0;
}
</style>
