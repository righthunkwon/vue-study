<template>
  <div>
    <h2>msg1</h2>
    <div>{{ msg1 }}</div>
    <div>{{ reversedMsg1 }}</div>
    <h2>msg2</h2>
    <div>{{ msg2 }}</div>
    <div>{{ reversedMsg2 }}</div>
  </div>
</template>

<script setup>
import { ref, watch } from 'vue'

/**
 * 최초 실행시에는 reverseMsg1가 출력되지 않음
 * 반응형의 값이 한 번 변경이 일어나야 reverseMsg1이 출력됨
 *
 */
const msg1 = ref('Hello1')
const reversedMsg1 = ref('')
watch(msg1, (newValue) => {
  reversedMsg1.value = newValue.split('').reverse().join('')
})

/**
 * immediate 속성을 통해 최초 실행시에도 reverseMsg2가 출력됨
 *
 */
const msg2 = ref('Hello2')
const reversedMsg2 = ref('')
watch(
  msg2,
  (newValue) => {
    reversedMsg2.value = newValue.split('').reverse().join('')
  },
  { immediate: true }
)
</script>

<style lang="scss" scoped></style>
