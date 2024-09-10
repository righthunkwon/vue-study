<template>
  <div>
    <h2>computed</h2>
    <p>{{ firstName }}</p>
    <p>{{ lastName }}</p>
    <p>{{ fullName }}</p>
    <button @click="handleSetComputed">set computed</button>
  </div>
</template>

<script>
/**
 * computed
 * : get() - 값을 확인하거나 가져올 때(기본)
 * : set() - 값을 설정하거나 변경할 때(선택)
 */
import { ref, computed } from 'vue'

export default {
  setup() {
    const firstName = ref('정훈')
    const lastName = ref('권')
    const fullName = computed({
      get() {
        return lastName.value + ' ' + firstName.value
      },
      set(value) {
        ;[firstName.value, lastName.value] = value.split(' ')
      }
    })

    // computed set()
    const handleSetComputed = () => {
      fullName.value = 'jeonghun kwon'
    }

    return { firstName, lastName, fullName, handleSetComputed }
  }
}
</script>

<style lang="scss" scoped></style>
