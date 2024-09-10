<template>
  <div class="card">
    <div class="card-header">Provide Inject Component</div>
    <div class="card-content">
      <button class="card-button" @click="parentCount++">count up!</button> <ChildCard></ChildCard>
    </div>
  </div>
</template>

<script setup>
/**
 *  Provide
 *  : 부모 컴포넌트는 provide를 통해 원하는 계층에 있는 자식 컴포넌트에 데이터 전달 가능
 *    가령, ProvideInjectCard는 ChildCard를 거치지 않고 DeepChildCard에 데이터를 전달 가능
 *    이를 통해 Props Drilling의 문제를 해결할 수 있음
 *  : 자식 컴포넌트는 inject를 통해 부모 컴포넌트에서 전달된 데이터에 접근 가능
 *  : app 컴포넌트에서 provide 사용 시 모든 컴포넌트에서 데이터 사용 가능
 *
 */

import { provide, ref } from 'vue' // import provide
import ChildCard from './ChildCard.vue'

const parentStaticMsg = 'parent static msg'
const parentRefMsg = ref('parent ref msg')
const parentCount = ref(0)

// provide(key, value)
provide('parentStaticMsg', parentStaticMsg)
provide('parentRefMsg', parentRefMsg)
// provide('parentDefMsg', parentDefMsg) // default
provide('parentCount', parentCount)
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

.card-button {
  padding: 8px;
  margin: 12px 0px;
}
</style>
