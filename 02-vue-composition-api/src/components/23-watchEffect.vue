<template>
  <div>
    <form>
      <!-- lazy 수식어를 통해 input이 끝난 후 focus out될 때 업데이트 -->
      <div><input v-model.lazy="title" type="text" placeholder="Title" /></div>
      <div><textarea v-model.lazy="contents" name="" id="" placeholder="Contents"></textarea></div>
    </form>
    <button @click="save(title, contents)">save</button>
  </div>
</template>

<script setup>
/**
 * watch()
 *  - 반응성 데이터를 첫 번째 매개변수에 명시
 *  - 반응성 데이터의 변경을 감지해서 콜백함수를 실행
 *  - 기본적으로 초기에 실행되지는 않지만, immediate 속성을 통해 초기에 1회 실행 가능
 *
 * watchEffect()
 *  - 콜백 함수 내의 반응성 데이터를 자동으로 파악하여 감지(상대적으로 덜 명시적)
 *  - 콜백 함수 내의 반응성 데이터의 변화를 감지해서 콜백함수를 실행
 *  - 기본적으로 초기에 1회 실행
 *
 */
import { ref, watchEffect } from 'vue'

const title = ref('')
const contents = ref('')

const save = (title, contents) => {
  console.log(`save api call: title(${title}, contents(${contents})`)
}

/**
 * watchEffect()는 콜백함수 내에서
 * title.value나 contents.value와 같은 반응성 데이터를 자동으로 감지
 *
 */
watchEffect(() => {
  save(title.value, contents.value)
})
</script>

<style lang="scss" scoped></style>
