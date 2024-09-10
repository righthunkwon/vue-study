<template>
  <h2>반응형 메시지</h2>
  <div>{{ reactiveMsg }}</div>
  <button @click="addReactiveMsg">반응형 메시지 추가</button>

  <h2>일반 메시지</h2>
  <div>{{ normalMsg }}</div>
  <button @click="addNormalMsg">일반 메시지 추가</button>
</template>

<script>
/**
 * Composition API
 * : 1. Reactivity API (ref(), computed(), reactive(), watch(), readonly(), ...)
 * : 2. Lifecycle hooks (setup, created, mounted, updated, unmounted, ...)
 * : 3. Dependency Injection (provide(), inject(), ...)
 *
 */
import { ref, isRef, onMounted, onBeforeMount } from 'vue'

export default {
  setup() {
    // 일반 메시지
    let normalMsg = 'Normal message'
    const addNormalMsg = () => {
      normalMsg = normalMsg + '!' // 추가안됨
    }

    // 반응형 메시지(ref)
    const reactiveMsg = ref('Reactive message')
    const addReactiveMsg = () => {
      reactiveMsg.value = reactiveMsg.value + '!' // 추가됨
    }

    // 반응형 확인
    console.log('isRef(reactviceMsg):', isRef(reactiveMsg)) // true
    console.log('isRef(normalMsg):', isRef(normalMsg)) // false

    // 라이프사이클
    // setup → beforeCreate → created → beforeMount → mounted → (beforeUpdate → updated) → beforeUnmount → unmounted
    console.log('1. setup()')
    onBeforeMount(() => {
      console.log('2. onBeforeMount()')
    })
    onMounted(() => {
      console.log('3. onMounted()')
    })
    return { reactiveMsg, normalMsg, addReactiveMsg, addNormalMsg }
  }
}
</script>

<style scoped></style>
