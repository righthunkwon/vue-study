<template>
  <h1>템플릿문법</h1>
  <hr />

  <!-- //////////////////////////////////////////////////////////////////////////////// -->
  <h2>1. 텍스트 보간법</h2>
  <p>normal msg: {{ msg }}</p>
  <p v-once>v-once msg: {{ msg }}</p>
  <button @click="addMsg">addMsg</button>
  <hr />

  <!-- //////////////////////////////////////////////////////////////////////////////// -->
  <h2>2. v-html (HTML 렌더링)</h2>
  <p>
    <span>텍스트 보간법(겹중괄호): </span>
    <span>{{ rawHtml }}</span>
  </p>
  <p>
    <span>v-html: </span>
    <span v-html="rawHtml"></span>
  </p>
  <hr />

  <!-- //////////////////////////////////////////////////////////////////////////////// -->
  <h2>3. v-bind (속성 바인딩)</h2>
  <!-- 1. title-->
  <div title="normal title">마우스를 올려보세요.</div>
  <div :title="dynamicTitle">마우스를 올려보세요.</div>
  <br />

  <!-- 2. input -->
  <input type="text" value="입력 불가" :disabled="isInputDisabled" />

  <!-- 3. input -->
  <!-- 다중속성 바인딩의 경우 단축표기 불가 -->
  <input v-bind="attrs" />

  <!-- 4. {{}} -->
  <!-- 이중 중괄호 내부에서는 자바스크립트 표현식 사용 가능 -->
  <p>
    <span>message ↔ </span><span>{{ msg.split('').reverse().join('') }}</span>
  </p>
  <p>{{ isInputDisabled ? 'input 비활성화' : 'input 활성화' }}</p>

  <hr />
</template>

<script>
/**
 * 템플릿 문법(Template Syntax)
 * : 텍스트 보간법 (이중 중괄호 {{ }}를 통한 데이터 바인딩, 속성이 변경될 때마다 갱신)
 * : v-once (일회성 보간, 초기 렌더링 이후에는 데이터가 변경되어도 갱신되지 않음)
 * : v-html (데이터를 html로 해석(기존 보간법에서는 데이터를 일반 텍스트로 해석), XSS 취약점에 유의)
 * : v-bind (속성 바인딩, 단축표기 지원(v-bind:title → :title), 다중속성 바인딩 지원(여러 속성을 객체로 만들어 넣어줌))
 */

import { ref } from 'vue'

export default {
  setup() {
    // 1. 텍스트 보간법
    const msg = ref('message')
    const addMsg = () => {
      msg.value = msg.value + '!'
    }

    // 2. v-html
    const rawHtml = ref('<b>rawHtml</b>')

    // 3. v-bind
    const dynamicTitle = ref('v-bind title')
    const isInputDisabled = ref(true)
    const attrs = ref({
      type: 'password',
      value: '패스워드를 입력하세요.',
      disabled: false
    })

    return {
      msg,
      addMsg,
      rawHtml,
      dynamicTitle,
      isInputDisabled,
      attrs
    }
  }
}
</script>

<style scoped></style>
