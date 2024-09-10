<template>
  <div>
    <input v-model="inputValue1" />
    <input v-model.lazy="inputValue2" />
    <input v-model.number="inputValue3" />
    <input v-model.trim="inputValue4" />
    <div>inputValue1: {{ inputValue1 }} - {{ typeof inputValue1 }}</div>
    <div>inputValue2: {{ inputValue2 }} - {{ typeof inputValue2 }}</div>
    <div>inputValue3: {{ inputValue3 }} - {{ typeof inputValue3 }}</div>
    <div>inputValue4: {{ inputValue4 }} - {{ typeof inputValue4 }}</div>
  </div>
</template>

<script setup>
/**
 * .lazy
 *  - input 완료 후 change 이벤트 이후에 동기화
 *
 * .number
 *  - 사용자 입력 후 자동으로 number 타입으로 형변환
 *
 * .trim
 *  - 사용자 입력 내용에서 자동으로 앞 뒤 공백 제거
 */
import { ref } from 'vue'

const inputValue1 = ref('')
const inputValue2 = ref('')
const inputValue3 = ref('')
const inputValue4 = ref('')
</script>

<style lang="scss" scoped></style>
