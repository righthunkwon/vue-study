<template>
  <div>
    <!-- 1. {{}}} & v-text  -->
    <!-- 데이터 출력-->
    <p>{{ msg }}</p>
    <p v-text="msg"></p>
    <hr />

    <!-- 2. v-html -->
    <!-- html 문서를 해석하고 표현 -->
    {{ htmlMsg }}
    <p v-text="htmlMsg"></p>
    <p v-html="htmlMsg"></p>
    <hr />

    <!-- 3. v-once -->
    <!-- 초기 렌더링만 수행, 성능 최적화와 관련 -->
    {{ msg }}
    <p v-once>{{ msg }}</p>
    <button @click="addMsg">! 추가</button>
    <hr />
  </div>
</template>

<script>
import { ref } from 'vue'

/**
 * 디렉티브(directives)
 * : v- 접두사가 있는 특수 속성
 * : 기능상에서 중요한 역할을 맡는 컴포넌트에게 '~하게 작동하라'고 지시하는 지시문
 * : v-text, v-html, v-if, v-show, v-for, v-on(@), v-bind(:), v-slot(#) 등 다양한 디렉티브 존재
 *
 */

export default {
  setup() {
    const msg = ref('안녕하세요!')
    const htmlMsg = ref('<strong>안녕하세요!</strong>')
    const addMsg = () => {
      msg.value += '!'
    }

    return { msg, htmlMsg, addMsg }
  }
}
</script>

<style lang="scss" scoped></style>
