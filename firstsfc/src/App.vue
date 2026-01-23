<template>
  <div class="app-container">
    <resume-website />
    <section class="food-section">
      <h2>Food Items</h2>
      <div class="food-items">
        <food-item />
        <food-item2 />
      </div>
    </section>
  </div>
</template>

<script>
import ResumeWebsite from './components/ResumeWebsite.vue'
import FoodItem from './components/FoodItem.vue'
import FoodItem2 from './components/FoodItem2.vue'

export default {
  components: {
    ResumeWebsite,
    FoodItem,
    FoodItem2
  }
}
</script>

<style>
body {
  margin: 0;
  padding: 0;
  background-color: #fff;
}

.app-container {
  width: 100%;
}

.resume-container {
  width: 100%;
  height: 100vh;
}

.food-section {
  padding: 40px 20px;
  text-align: center;
  background-color: #f4f4f4;
}

.food-section h2 {
  font-size: 2em;
  margin-bottom: 30px;
  color: #333;
}

.food-items {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  gap: 20px;
}
</style>