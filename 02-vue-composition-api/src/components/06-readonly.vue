<template>
  <div>
    <h2>readonly</h2>
    <p>original {{ original }}</p>
    <p>copy(readonly) {{ copy }}</p>
  </div>
</template>

<script>
/**
 * readonly
 * : 반응형 객체의 변경 방지
 * : 개발을 진행하다 보면 반응형 객체(ref, reactive의 변화를 추적하기를 원하면서도,
 *   특정 부분에서는 변화를 막기를 원하는데, 바로 이때 readonly를 통해 반응형 객체의 변경을 방지할 수 있다.
 *
 */
import { reactive, readonly } from 'vue'

export default {
  setup() {
    const original = reactive({
      count: 0
    })
    const copy = readonly(original)

    // 원본 변경 시 복사본에 의존하는 watch도 트리거되어 복사본도 변경
    original.count++
    console.log('original', original.count) // 1
    console.log('copy', copy.count) // 1

    original.count++
    console.log('original', original.count) // 2
    console.log('copy', copy.count) // 2

    original.count++
    console.log('original', original.count) // 3
    console.log('copy', copy.count) // 3

    // readonly
    // 복사본 및 복사본과 연결된 원본 변경 불가
    copy.count++
    copy.count++
    copy.count++
    copy.count++
    copy.count++
    console.log('copy', copy.count) // 3

    // 원본 변경 시 복사본에 의존하는 watch도 트리거되어 복사본도 변경
    original.count++
    console.log('original', original.count) // 4
    console.log('copy', copy.count) // 4

    return { original, copy }
  }
}
</script>

<style lang="scss" scoped></style>
