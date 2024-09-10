<template>
  <h2>normalObj</h2>
  <p>name1: {{ name1 }}</p>
  <p>birth1: {{ birth1 }}</p>

  <h2>destructuringObj</h2>
  <p>name2: {{ name2 }}</p>
  <p>birth2: {{ birth2 }}</p>
</template>

<script>
import { reactive, toRefs } from 'vue'

export default {
  setup() {
    // 일반적인 구조분해할당을 할 경우 반응형 객체는 반응형 연결을 잃게 됨
    const normalObj = reactive({
      name1: 'Kwon1',
      birth1: '19961'
    })
    const { name1, birth1 } = normalObj // 구조분해할당

    // toRef, toRefs를 통해 구조분해할당을 할 경우 객체의 속성과 동기화되어 반응형 연결을 유지
    const destructuringObj = reactive({
      name2: 'Kwon2',
      birth2: '19962'
    })
    const { name2, birth2 } = toRefs(destructuringObj) // toRefs 구조분해할당

    console.log(typeof normalObj) // object
    console.log(typeof name1.value) // undefined
    console.log(typeof birth1.value) // undefined

    console.log(typeof destructuringObj) // object
    console.log(typeof name2.value) // string (Ref)
    console.log(typeof birth2.value) // string (Ref)

    return { name1, birth1, name2, birth2, normalObj, destructuringObj }
  }
}
</script>

<style lang="scss" scoped></style>
s
