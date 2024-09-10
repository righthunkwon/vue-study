<template>
  <div></div>
</template>

<script setup>
import { reactive, watch } from 'vue'

/**
 * 1. watch(obj)
 * - 감지 가능
 * - 단, obj는 참조타입이므로 결국 동일한 객체이므로 동일한 값이 찍힘
 * - 반응형 객체를 직접 watch()하면 암시적으로 깊은 감시자가 생성되어
 *   '객체 내의 객체'와 같은 모든 중첩된 속성에도 트리거
 */
const obj = reactive({
  count: 0
})
// watch(obj, (newValue, oldValue) => {
//   console.log('newValue', newValue)
//   console.log('oldValue', oldValue)
// })

/**
 * 2. watch(obj.property)
 * - 감지 불가
 * - obj.count는 반응형이 아니기 때문
 * - console.log(typeof obj.count) // number
 */
// watch(obj.count, (newValue, oldValue) => {
//   console.log('newValue', newValue)
//   console.log('oldValue', oldValue)
// })

/**
 * 3. watch(obj.property)
 * - getter 함수 활용 시 감지 가능
 */
watch(
  () => obj.count,
  (newValue, oldValue) => {
    console.log('newValue', newValue)
    console.log('oldValue', oldValue)
  }
)
</script>

<style lang="scss" scoped></style>
