<template>
  <div class="card">
    <div class="card-header">Deep Child Component</div>
    <div class="card-content">
      <p>{{ p1 }}</p>
      <p>{{ p2 }}</p>
      <p>{{ p3 }}</p>
      <p>parent count : {{ p4 }}</p>
    </div>
  </div>
</template>

<script setup>
import { inject } from 'vue' // import inject

// inject(key, [default Msg])
const p1 = inject('parentStaticMsg')
const p2 = inject('parentRefMsg')
const p3 = inject('parentDefMsg', 'parent default msg') // default
const p4 = inject('parentCount')
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
