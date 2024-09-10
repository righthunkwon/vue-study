<template>
  <div></div>
</template>

<script setup>
/**
 * watch
 *  - 반응형 상태가 변경되었을 때 작업을 수행하기 위해 사용
 *  - 첫 번째 인자로는 감시할 대상을, 두 번째 인자로는 변경된 값과 이전 값을 인자로 갖는 콜백함수를 가지며,
 *    감시할 대상이 변경될 경우 콜백함수를 실행하는 구조
 *
 */
import { ref, watch } from 'vue'

/**
 * watch()
 *
 */
const msg = ref('')
watch(msg, (newValue, oldValue) => {
  console.log('newValue', newValue)
  console.log('oldValue', oldValue)
})

/**
 * watch([])
 *
 */
const var1 = ref(0)
const var2 = ref(0)
watch([var1, var2], ([newVar1, newVar2]) => {
  console.log(newVar1, newVar2)
})
</script>

<style lang="scss" scoped></style>
