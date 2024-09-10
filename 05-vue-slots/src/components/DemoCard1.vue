<template>
  <div class="card">
    <!-- 1. header-->
    <div class="card-header">
      <slot name="header"></slot>
    </div>
    <!-- 2. content -->
    <div class="card-content">
      <slot name="content"></slot>
    </div>
    <!-- 3. footer -->
    <div class="card-footer">
      <slot name="footer"></slot>
    </div>
  </div>
</template>

<script setup></script>

<style scoped>
.card {
  width: 600px;
  border: 2px solid gray;
}

.card-header {
  padding: 12px;
  background-color: lightgray;
}

.card-content {
  padding: 40px 12px;
  background-color: whitesmoke;
}

.card-footer {
  padding: 12px;
  background-color: lightgray;
}
</style>
