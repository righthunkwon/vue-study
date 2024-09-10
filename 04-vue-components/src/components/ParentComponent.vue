<template>
  <div><ChildCompoment @child-event="childEvent" /></div>
</template>

<script setup>
/**
 * $emit
 *  - 자식 컴포넌트는 내장 메서드 $emit을 사용하여 부모 컴포넌트에게 이벤트를 발신
 *  - 부모 컴포넌트는 v-on(@)을 사용하여 자식 컴포넌트에서 전송된 이벤트를 수신
 *  - 이때, 이벤트 이름은 자동 대소문자 변환을 제공하여,
 *    자식에서 camelCase 형식으로 전달한 이벤트를
 *    부모에서는 kebab-case 형식으로 이를 수신할 수 있음
 *  - props 케이싱과 마찬가지로 템플릿에서는 kebab-case 형식의 이벤트 리스너를 사용하는 것을 권장
 *
 */
import ChildCompoment from './ChildCompoment.vue'

const childEvent = (p1, p2, p3) => {
  console.log('childEvent 수신')
  console.log(p1) // child param1
  console.log(p2) // child param2
  console.log(p3) // child param3
}
</script>

<style lang="scss" scoped></style>
