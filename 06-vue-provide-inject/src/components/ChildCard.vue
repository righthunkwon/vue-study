<template>
  <div class="card">
    <div class="card-header">Child Component</div>
    <div class="card-content"><DeepChildCard></DeepChildCard></div>
  </div>
</template>

<script setup>
import DeepChildCard from './DeepChildCard.vue'
</script>

<style scoped>
.card {
  width: 80%;
  border: 2px solid gray;
}

.card-header {
  font-weight: 600;
  padding: 12px 20px;
  background-color: lightgray;
}

.card-content {
  padding: 40px;
}
</style>
